# Markdown Structure Linter

Markdown Structure Linter is a tool designed to validate the structure of markdown files against predefined templates. It ensures that your markdown documents adhere to specific structural requirements, making it ideal for maintaining consistency in documentation across projects.

## Features

- Validate markdown files against custom templates
- Check for required sections, paragraph counts, and code block requirements
- Flexible template definitions using YAML
- Output results in both human-readable text and structured JSON formats
- Provide precise location information with start and end character indexes for each heading
- Can be used as a CLI tool or imported as a module in other projects

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/your-username/markdown-structure-linter.git
   cd markdown-structure-linter
   ```

2. Install dependencies:
   ```
   npm install
   ```

## Usage

### As a CLI Tool

To use the Markdown Structure Linter as a CLI tool, you need a markdown file to lint and a template to lint against. The basic command structure is:

```
node index.js --file <path-to-markdown> --template <template-name>
```

#### Options

- `--file` or `-f`: Path to the markdown file to lint (required)
- `--template` or `-t`: Name of the template to use (required)
- `--json`: Output results in JSON format (optional)

#### Examples

1. Lint a markdown file using the "How-to" template:
   ```
   node index.js --file ./docs/how-to-guide.md --template How-to
   ```

2. Lint a markdown file and output results in JSON format:
   ```
   node index.js --file ./docs/api-reference.md --template API-doc --json
   ```

### As a Module

You can also use the Markdown Structure Linter as a module in your Node.js projects. First, install it as a dependency:

```
npm install markdown-structure-linter
```

Then, you can import and use it in your JavaScript code:

```javascript
import { markdownStructureLinter } from 'markdown-structure-linter';

const markdownContent = '# Your Markdown Content\n\nSome text here...';
const templateName = 'Your-Template-Name';

// For text output
const textResult = markdownStructureLinter(markdownContent, templateName);
console.log(textResult);

// For JSON output
const jsonResult = markdownStructureLinter(markdownContent, templateName, 'json');
console.log(JSON.stringify(jsonResult, null, 2));
```

## Templates

Templates are defined in the `templates.yaml` file. Each template specifies the expected structure of a markdown document, including:

- Required sections
- Paragraph count limits
- Code block requirements
- Nested section structures

For more information on creating and modifying templates, refer to the comments in the `templates.yaml` file.

## Output

### Text Output (Default)

When used without specifying JSON output, the linter provides human-readable output:

```
Structure violations found:
[Introduction] (start: 0, end: 150): Expected at least 2 paragraphs, but found 1
[Usage] (start: 151, end: 500): Missing required section "Examples"
```

### JSON Output

When JSON output is specified, the linter returns a structured object:

```json
{
  "success": false,
  "errors": [
    {
      "head": "Introduction",
      "startIndex": 0,
      "endIndex": 150,
      "message": "Expected at least 2 paragraphs, but found 1"
    },
    {
      "head": "Usage",
      "startIndex": 151,
      "endIndex": 500,
      "message": "Missing required section \"Examples\""
    }
  ]
}
```

The `startIndex` and `endIndex` properties provide the character positions of the start and end of each section, allowing for precise location of issues within the document.

## Contributing

Contributions to the Markdown Structure Linter are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.