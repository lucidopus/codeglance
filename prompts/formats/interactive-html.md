# CodeGlance Interactive HTML Output Prompt

You are generating an interactive HTML documentation with embedded JavaScript for enhanced navigation and visualization.

## Input Repository
Analyze the repository at: [REPOSITORY_PATH]

## HTML Documentation Structure

### Main HTML Template
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CodeGlance - [Project Name]</title>
    <style>
        /* Modern, responsive styling */
        :root {
            --primary: #007bff;
            --secondary: #6c757d;
            --success: #28a745;
            --dark: #343a40;
            --light: #f8f9fa;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
        }
        
        .sidebar {
            position: fixed;
            width: 250px;
            height: 100vh;
            background: var(--dark);
            overflow-y: auto;
        }
        
        .main-content {
            margin-left: 250px;
            padding: 2rem;
        }
        
        .collapsible {
            cursor: pointer;
            padding: 0.5rem;
            background: var(--light);
            border: none;
            width: 100%;
            text-align: left;
        }
        
        .collapsible:hover {
            background: #e9ecef;
        }
        
        .content {
            display: none;
            padding: 1rem;
            background: white;
            border-left: 3px solid var(--primary);
        }
        
        .search-box {
            padding: 1rem;
            width: 100%;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        
        .tab-container {
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        
        .tab-buttons {
            display: flex;
            background: var(--light);
        }
        
        .tab-button {
            padding: 0.5rem 1rem;
            border: none;
            background: transparent;
            cursor: pointer;
        }
        
        .tab-button.active {
            background: white;
            border-bottom: 2px solid var(--primary);
        }
        
        .tab-content {
            padding: 1rem;
        }
        
        .tab-pane {
            display: none;
        }
        
        .tab-pane.active {
            display: block;
        }
        
        pre {
            background: #f4f4f4;
            padding: 1rem;
            border-radius: 4px;
            overflow-x: auto;
        }
        
        .tree-view {
            font-family: monospace;
        }
        
        .tree-item {
            cursor: pointer;
            padding: 0.25rem;
        }
        
        .tree-item:hover {
            background: var(--light);
        }
        
        .diagram-container {
            border: 1px solid #ddd;
            padding: 1rem;
            border-radius: 4px;
            margin: 1rem 0;
        }
        
        .metrics-card {
            background: white;
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 1rem;
            margin: 0.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: #e9ecef;
            border-radius: 10px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: var(--success);
            transition: width 0.3s ease;
        }
    </style>
</head>
<body>
```

### Interactive Navigation Sidebar
```html
<nav class="sidebar">
    <div style="padding: 1rem; color: white;">
        <h2>📚 CodeGlance</h2>
        <input type="text" class="search-box" placeholder="Search documentation..." id="searchBox">
    </div>
    
    <ul style="list-style: none; padding: 0;">
        <li><a href="#overview">🏠 Overview</a></li>
        <li><a href="#architecture">🏗️ Architecture</a></li>
        <li><a href="#components">🧩 Components</a></li>
        <li><a href="#api">🔌 API Reference</a></li>
        <li><a href="#database">💾 Database</a></li>
        <li><a href="#deployment">🚀 Deployment</a></li>
    </ul>
</nav>
```

### Interactive Components

#### 1. Collapsible Sections
```html
<button class="collapsible">📁 Project Structure</button>
<div class="content">
    <pre class="tree-view">
src/
├── components/
│   ├── Button.jsx
│   └── Card.jsx
├── services/
│   └── api.js
└── utils/
    └── helpers.js
    </pre>
</div>
```

#### 2. Tabbed Interface
```html
<div class="tab-container">
    <div class="tab-buttons">
        <button class="tab-button active" onclick="showTab('overview')">Overview</button>
        <button class="tab-button" onclick="showTab('code')">Code</button>
        <button class="tab-button" onclick="showTab('tests')">Tests</button>
    </div>
    
    <div class="tab-content">
        <div id="overview" class="tab-pane active">
            <h3>Component Overview</h3>
            <p>Description and usage...</p>
        </div>
        <div id="code" class="tab-pane">
            <pre><code>// Component code here</code></pre>
        </div>
        <div id="tests" class="tab-pane">
            <pre><code>// Test code here</code></pre>
        </div>
    </div>
</div>
```

#### 3. Interactive Diagrams
```html
<div class="diagram-container">
    <canvas id="architectureDiagram"></canvas>
</div>

<script>
// Interactive architecture diagram
const canvas = document.getElementById('architectureDiagram');
const ctx = canvas.getContext('2d');

// Draw interactive components
function drawArchitecture() {
    // Drawing code here
}

canvas.addEventListener('click', (e) => {
    // Handle clicks on diagram elements
});
</script>
```

#### 4. Search Functionality
```javascript
<script>
document.getElementById('searchBox').addEventListener('input', (e) => {
    const searchTerm = e.target.value.toLowerCase();
    const sections = document.querySelectorAll('.searchable');
    
    sections.forEach(section => {
        const text = section.textContent.toLowerCase();
        if (text.includes(searchTerm)) {
            section.style.display = 'block';
            // Highlight matching text
            highlightText(section, searchTerm);
        } else {
            section.style.display = 'none';
        }
    });
});

function highlightText(element, searchTerm) {
    const innerHTML = element.innerHTML;
    const index = innerHTML.toLowerCase().indexOf(searchTerm);
    if (index >= 0) {
        element.innerHTML = innerHTML.substring(0, index) + 
            '<mark>' + innerHTML.substring(index, index + searchTerm.length) + '</mark>' + 
            innerHTML.substring(index + searchTerm.length);
    }
}
</script>
```

#### 5. Metrics Dashboard
```html
<div class="metrics-dashboard">
    <div class="metrics-card">
        <h4>Code Coverage</h4>
        <div class="progress-bar">
            <div class="progress-fill" style="width: 85%"></div>
        </div>
        <span>85%</span>
    </div>
    
    <div class="metrics-card">
        <h4>Test Status</h4>
        <div style="color: var(--success);">✅ All tests passing</div>
    </div>
    
    <div class="metrics-card">
        <h4>Dependencies</h4>
        <ul>
            <li>Total: 45</li>
            <li>Outdated: 3</li>
            <li>Vulnerabilities: 0</li>
        </ul>
    </div>
</div>
```

#### 6. Code Explorer
```html
<div class="code-explorer">
    <div class="file-tree">
        <!-- Interactive file tree -->
    </div>
    <div class="code-viewer">
        <pre><code class="language-javascript" id="codeDisplay">
        // Code will be displayed here
        </code></pre>
    </div>
</div>

<script>
function loadFile(filepath) {
    // Load and display file content
    document.getElementById('codeDisplay').textContent = fileContents[filepath];
    // Apply syntax highlighting
    Prism.highlightElement(document.getElementById('codeDisplay'));
}
</script>
```

### JavaScript Enhancements
```javascript
<script>
// Collapsible functionality
document.querySelectorAll('.collapsible').forEach(button => {
    button.addEventListener('click', () => {
        button.classList.toggle('active');
        const content = button.nextElementSibling;
        content.style.display = content.style.display === 'block' ? 'none' : 'block';
    });
});

// Tab functionality
function showTab(tabName) {
    document.querySelectorAll('.tab-pane').forEach(pane => {
        pane.classList.remove('active');
    });
    document.getElementById(tabName).classList.add('active');
    
    document.querySelectorAll('.tab-button').forEach(button => {
        button.classList.remove('active');
        if (button.textContent.toLowerCase().includes(tabName)) {
            button.classList.add('active');
        }
    });
}

// Smooth scrolling
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
    });
});

// Copy code buttons
document.querySelectorAll('pre').forEach(pre => {
    const button = document.createElement('button');
    button.textContent = '📋 Copy';
    button.style.position = 'absolute';
    button.style.top = '5px';
    button.style.right = '5px';
    button.onclick = () => {
        navigator.clipboard.writeText(pre.textContent);
        button.textContent = '✅ Copied!';
        setTimeout(() => button.textContent = '📋 Copy', 2000);
    };
    pre.style.position = 'relative';
    pre.appendChild(button);
});

// Generate table of contents
function generateTOC() {
    const toc = document.createElement('div');
    toc.className = 'table-of-contents';
    const headings = document.querySelectorAll('h2, h3');
    
    headings.forEach(heading => {
        const link = document.createElement('a');
        link.href = '#' + heading.id;
        link.textContent = heading.textContent;
        link.style.marginLeft = heading.tagName === 'H3' ? '20px' : '0';
        toc.appendChild(link);
        toc.appendChild(document.createElement('br'));
    });
    
    return toc;
}

// Initialize on load
document.addEventListener('DOMContentLoaded', () => {
    // Add IDs to headings
    document.querySelectorAll('h2, h3').forEach((heading, index) => {
        heading.id = 'heading-' + index;
    });
    
    // Insert TOC
    const tocContainer = document.getElementById('toc');
    if (tocContainer) {
        tocContainer.appendChild(generateTOC());
    }
});
</script>
```

## Features to Include

1. **Interactive Navigation**: Sidebar with search and filtering
2. **Collapsible Sections**: For managing large content
3. **Syntax Highlighting**: Using Prism.js or highlight.js
4. **Interactive Diagrams**: Using Canvas or SVG
5. **Search Functionality**: Real-time search with highlighting
6. **Code Examples**: With copy buttons
7. **Metrics Dashboard**: Visual project statistics
8. **Responsive Design**: Mobile-friendly layout
9. **Dark Mode Toggle**: User preference support
10. **Export Options**: Print-friendly version

## Output Files

Generate the following:
- `guide/index.html` - Main documentation
- `guide/assets/style.css` - Styles
- `guide/assets/script.js` - Interactive features
- `guide/data/content.json` - Documentation data

Generate interactive HTML documentation for [REPOSITORY_PATH] now.