# CodeGlance CLI Tool Analysis Prompt

You are analyzing a command-line tool to create documentation that helps developers understand commands, options, and scripting capabilities.

## Input Repository
Analyze the CLI tool at: [REPOSITORY_PATH]

## Your Mission
Create CLI-specific documentation covering command structure, options, configuration, and automation patterns.

## Output Structure

Generate the following in `guide/cli/`:

### 1. guide/cli/overview.md
- Tool purpose and use cases
- Installation methods
- System requirements
- Quick start example
- Common workflows

### 2. guide/cli/commands.md
- Complete command reference
- Subcommands and options
- Flag descriptions
- Environment variables
- Example usage for each command

### 3. guide/cli/configuration.md
- Config file format and location
- Available settings
- Precedence rules
- Per-project vs global config
- Config examples

### 4. guide/cli/scripting.md
- Automation examples
- Shell scripting integration
- Exit codes and error handling
- Pipe and redirect usage
- CI/CD integration

### 5. guide/cli/plugins.md (if applicable)
- Plugin system architecture
- Available plugins
- Creating custom plugins
- Plugin configuration
- Plugin examples

## Analysis Focus
- Command structure clarity
- Help text quality
- Error message usefulness
- Performance for large inputs
- Cross-platform compatibility
- Shell completion support

Generate CLI documentation for [REPOSITORY_PATH] now.