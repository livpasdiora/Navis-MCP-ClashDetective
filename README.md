# MCP-Navisworks Integration for AI-Assisted MEP Coordination

MCP server integrating Claude AI with Autodesk Navisworks for MEP coordination. Enables natural language interaction for model recognition, intelligent clash grouping, and resolution suggestions via Clash Detective integration.

## Overview

This project implements a three-layer architecture connecting Large Language Models with BIM coordination software:

- **AI Interface**: Anthropic's Claude as MCP client
- **MCP Server**: Node.js/TypeScript managing communication
- **Navisworks Plugin**: C# plugin using Navisworks API

## Features

### Original Implementation (by Kikki - https://github.com/kikki/MCP-Add-in-Autodesk_Navisworks_Manage_2026/tree/main)
- **Model Overview**: Automatic identification of loaded disciplines and element counts
- **Element Queries**: List properties of specific items by canonical ID
- **Selection Control**: Select elements through natural language commands

### Extended Implementation (this work)
- **Clash Detective Integration**: Access existing clash tests and read results directly
- **Intelligent Conflict Grouping**: AI-powered analysis to group and prioritize clashes
- **Resolution Suggestions**: Context-aware recommendations for clash resolution

## Requirements

- Autodesk Navisworks Manage 2026
- Node.js 18+
- Claude Desktop (or other MCP-compatible client)
- .NET Framework 4.8

## Usage

1. Open your federated model in Navisworks Manage
2. Ensure the MCP plugin is loaded (check Navisworks Add-ins)
3. Start Claude Desktop
4. Interact using natural language:
```
"Which disciplines are loaded in this model and how many elements does each have?"

"Access through Clash Detective the test named PLUM vs ALL"

"Group similar conflicts by Element ID and organize by criticality"
```

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Claude Desktop │────▶│   MCP Server    │────▶│   Navisworks    │
│   (AI Client)   │◀────│  (Node.js/TS)   │◀────│   Plugin (C#)   │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                              JSON-RPC              Navisworks API
```

## Limitations

- Element counting works best with standard Revit families; fabrication parts may show less detail
- Clash detection relies on Navisworks' native Clash Detective (manual test setup required)
- Spatial reasoning for complex conflicts requires detailed contextual information
- System effectiveness depends on BIM model quality and naming conventions

## Acknowledgments

This project extends [Kikki's MCP-Navisworks proof-of-concept]([https://github.com/user/repo](https://github.com/kikki/MCP-Add-in-Autodesk_Navisworks_Manage_2026/tree/main)), which established basic communication between MCP and Autodesk Navisworks 2026, including model overview, element queries, and selection control functionalities. The Clash Detective integration for intelligent clash grouping and resolution optimization was developed as part of this research.

## Academic Context

Developed as part of doctoral research at the Federal University of Paraná (UFPR), Graduate Program in Civil Engineering. This work was supported by CAPES (Coordination for the Improvement of Higher Education Personnel – Brazil).

### Citation

If you use this work in your research, please cite us! 

```

## License

MIT License - see [LICENSE](LICENSE) for details.

## Contact

**Livia Pasdiora**  
Federal University of Paraná  
liviapasdiora@ufpr.br - liviapasdiora@gmail.com
