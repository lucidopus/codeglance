# Codeglance Gemini CLI Slash Command

## /codeglance

Execute a comprehensive code analysis workflow on a GitHub repository. This command clones a repository and runs a complete analysis using the available prompts.

### Usage

```
/codeglance <github_url>
```

**Example:**
```
/codeglance https://github.com/username/repository-name
```

### Implementation

```javascript
// /codeglance slash command implementation
async function codeglance(github_url, options = {}) {
  const { branch = 'main' } = options;
  
  // Validate GitHub URL format
  const urlPattern = /^https:\/\/github\.com\/[\w\-\.]+\/[\w\-\.]+(?:\/.*)?$/;
  if (!urlPattern.test(github_url)) {
    throw new Error('Invalid GitHub URL format. Please provide a valid GitHub repository URL.');
  }
  
  // Extract repository name from URL
  const repoName = github_url.split('/').pop().replace('.git', '');
  const repoPath = `repos/${repoName}`;
  
  console.log(`=€ Starting Codeglance analysis for: ${github_url}`);
  
  try {
    // Step 1: Repository Setup
    console.log('=Á Setting up repository...');
    
    // Create repos directory if it doesn't exist
    await runShellCommand('mkdir -p repos');
    
    // Check if repository already exists
    const repoExists = await checkPath(`repos/${repoName}`);
    if (repoExists) {
      console.log(`   Repository already exists at repos/${repoName}. Using existing copy.`);
      process.chdir(repoPath);
    } else {
      // Clone repository
      const cloneCmd = branch !== 'main' 
        ? `git clone -b ${branch} ${github_url} ${repoPath}`
        : `git clone ${github_url} ${repoPath}`;
        
      await runShellCommand(cloneCmd);
      console.log(' Repository cloned successfully');
      process.chdir(repoPath);
    }
    
    // Verify repository structure
    await runShellCommand('ls -la');
    
    // Create codeglance-results directory
    await runShellCommand('mkdir -p codeglance-results');
    await runShellCommand('mkdir -p guide');
    
    console.log('= Starting sequential prompt execution...');
    
    // Step 2: Sequential Prompt Execution
    const prompts = [
      {
        name: 'project-overview',
        description: 'Foundation Understanding',
        output: 'guide/overview.md'
      },
      {
        name: 'visual-tree',
        description: 'Structure Mapping',
        output: 'guide/tree.md'
      },
      {
        name: 'file-insights',
        description: 'Deep File Analysis',
        output: 'guide/file-insights.md'
      },
      {
        name: 'architecture',
        description: 'System Design',
        output: 'guide/architecture.md'
      },
      {
        name: 'quick-start',
        description: 'Developer Onboarding',
        output: 'guide/quick-start.md'
      },
      {
        name: 'master-analysis',
        description: 'Comprehensive Synthesis',
        output: 'Complete guide suite'
      }
    ];
    
    const results = [];
    const startTime = Date.now();
    
    for (let i = 0; i < prompts.length; i++) {
      const prompt = prompts[i];
      console.log(`\n=Ë Step ${i + 1}/6: ${prompt.description}`);
      console.log(`=' Executing /${prompt.name}...`);
      
      try {
        const promptStart = Date.now();
        
        // Execute the prompt (this would be implemented by the Gemini CLI system)
        await executePrompt(prompt.name);
        
        const promptEnd = Date.now();
        const duration = Math.round((promptEnd - promptStart) / 1000);
        
        console.log(` ${prompt.name} completed in ${duration}s`);
        console.log(`=Ä Output: ${prompt.output}`);
        
        results.push({
          step: i + 1,
          name: prompt.name,
          description: prompt.description,
          output: prompt.output,
          duration: duration,
          status: 'success',
          timestamp: new Date().toISOString()
        });
        
      } catch (error) {
        console.log(`L ${prompt.name} failed: ${error.message}`);
        
        results.push({
          step: i + 1,
          name: prompt.name,
          description: prompt.description,
          output: prompt.output,
          duration: 0,
          status: 'failed',
          error: error.message,
          timestamp: new Date().toISOString()
        });
        
        // Continue with remaining prompts
        continue;
      }
    }
    
    const totalTime = Math.round((Date.now() - startTime) / 1000);
    
    // Generate execution summary
    await generateExecutionSummary(results, totalTime, github_url, repoName);
    
    console.log('\n<‰ Codeglance analysis completed!');
    console.log(`ñ  Total execution time: ${totalTime}s`);
    console.log(`=Ê Results: ${results.filter(r => r.status === 'success').length}/${results.length} prompts succeeded`);
    
    // Display results summary
    displayResultsSummary(results, repoPath);
    
  } catch (error) {
    console.error('=¥ Codeglance execution failed:', error.message);
    throw error;
  }
}

// Helper function to execute individual prompts
async function executePrompt(promptName) {
  // This would be implemented by the Gemini CLI system
  // to execute the actual prompt files
  return new Promise((resolve, reject) => {
    // Simulate prompt execution
    setTimeout(() => {
      console.log(`   Processing ${promptName}...`);
      resolve();
    }, 2000 + Math.random() * 3000);
  });
}

// Helper function to check if path exists
async function checkPath(path) {
  try {
    await runShellCommand(`test -d ${path}`);
    return true;
  } catch {
    return false;
  }
}

// Helper function to run shell commands
async function runShellCommand(command) {
  // This would be implemented by the Gemini CLI system
  console.log(`  $ ${command}`);
  return new Promise((resolve) => {
    setTimeout(() => resolve(), 500);
  });
}

// Generate execution summary
async function generateExecutionSummary(results, totalTime, githubUrl, repoName) {
  const successful = results.filter(r => r.status === 'success');
  const failed = results.filter(r => r.status === 'failed');
  
  const summary = `# Codeglance Analysis Summary

## Repository Information
- **Repository:** ${githubUrl}
- **Local Path:** repos/${repoName}
- **Analysis Date:** ${new Date().toISOString()}
- **Total Execution Time:** ${totalTime} seconds

## Execution Results
- **Total Steps:** ${results.length}
- **Successful:** ${successful.length}
- **Failed:** ${failed.length}

## Step Details

${results.map(r => `### ${r.step}. ${r.description} (${r.name})
- **Status:** ${r.status === 'success' ? ' Success' : 'L Failed'}
- **Duration:** ${r.duration}s
- **Output:** ${r.output}
${r.error ? `- **Error:** ${r.error}` : ''}
- **Timestamp:** ${r.timestamp}
`).join('\n')}

## Generated Documentation

${successful.map(r => `- [${r.description}](${r.output})`).join('\n')}

## Quick Access Commands

\`\`\`bash
# Navigate to repository
cd repos/${repoName}

# View all generated guides
ls -la guide/

# Open overview
cat guide/overview.md
\`\`\`

## Next Steps

${failed.length > 0 ? `### Failed Prompts
The following prompts failed and may need manual execution:
${failed.map(r => `- \`/${r.name}\` - ${r.error}`).join('\n')}

` : ''}### Recommendations
1. Review the generated documentation in the \`guide/\` directory
2. Use the quick-start guide to begin development
3. Refer to the architecture documentation for system understanding
4. Check file-insights for critical code analysis

---
Generated by Codeglance =
`;

  await saveToFile('codeglance-results/summary.md', summary);
  console.log('=Ë Execution summary saved to codeglance-results/summary.md');
}

// Display results summary in console
function displayResultsSummary(results, repoPath) {
  console.log('\n=Á Generated Documentation:');
  results
    .filter(r => r.status === 'success')
    .forEach(r => {
      console.log(`   =Ä ${r.output}`);
    });
  
  console.log('\n= Quick Access:');
  console.log(`   =Â Repository: ${repoPath}`);
  console.log(`   =Ë Summary: ${repoPath}/codeglance-results/summary.md`);
  console.log(`   =Ú Documentation: ${repoPath}/guide/`);
}

// Helper to save content to file
async function saveToFile(filepath, content) {
  // This would be implemented by the Gemini CLI system
  console.log(`  =¾ Saving to ${filepath}`);
  return Promise.resolve();
}

// Export the command
module.exports = {
  name: 'codeglance',
  description: 'Execute comprehensive code analysis workflow on a GitHub repository',
  usage: '/codeglance <github_url> [-b branch-name]',
  execute: codeglance
};
```

### Command Options

**Basic Usage:**
```
/codeglance https://github.com/user/repo
```

**With specific branch:**
```
/codeglance https://github.com/user/repo -b branch-name
```

### Workflow Overview

This command orchestrates the following sequential workflow:

1. **Repository Cloning** - Clone the GitHub repository to `repos/` directory
2. **Sequential Prompt Execution** - Run analysis prompts in optimal order:
   - `01-project-overview` ’ Foundation Understanding
   - `02-visual-tree` ’ Structure Mapping  
   - `03-file-insights` ’ Deep File Analysis
   - `04-architecture` ’ System Design
   - `05-quick-start` ’ Developer Onboarding
   - `06-master-analysis` ’ Comprehensive Synthesis
3. **Comprehensive Analysis** - Generate complete documentation and insights

### Expected Outputs

This workflow generates documentation in sequential order:
1. `guide/overview.md` - Project foundation and purpose
2. `guide/tree.md` - Visual directory structure
3. `guide/file-insights.md` - Critical file deep-dive
4. `guide/architecture.md` - System design and patterns
5. `guide/quick-start.md` - Developer onboarding guide
6. Complete guide suite with cross-references

### Error Handling

- Repository cloning failures provide clear error messages and troubleshooting steps
- Individual prompt failures are logged but don't stop the entire workflow
- Summary report includes both successful and failed operations
- Provides manual execution steps for failed prompts

### Integration with Existing Prompts

All prompts in the `prompts/` directory are designed to work with this orchestrator:

- `prompts/project-overview.md`
- `prompts/visual-tree.md`
- `prompts/file-insights.md`
- `prompts/architecture.md`
- `prompts/quick-start.md`
- `prompts/master-analysis.md`