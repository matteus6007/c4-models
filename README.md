# C4 Models

Context, Containers, Components and Code - https://c4model.com/ 

## Getting Started

Create diagrams using PlantUML - https://github.com/plantuml-stdlib/C4-PlantUML.

1. Create a `.puml` file using the following template:

```
@startuml <Name>

' Diagram Type
!include <Diagram_Type>

' C4 models

@enduml
```

2. Set diagram type:

  * Level 1: System Context diagram - https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml
  * Level 2: Container diagram - https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml
  * Level 3: Component diagram -https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Component.puml

3. Define C4 elements - https://github.com/plantuml-stdlib/C4-PlantUML#supported-diagram-types - to build Container diagram.

4. Optionally include a legend `LAYOUT_WITH_LEGEND()`

## Generating Images

### Online

Copy content from `.puml` file:

https://www.plantuml.com/plantuml

### Locally

Prerequisites:

* Install Java https://www.java.com/en/download/apple.jsp
* Install Graphviz `brew install graphviz`

See https://plantuml.com/starting for full options.

```
java -jar plantuml.jar file1 file2 file3
```

#### Previewing Images

Download VS Code PlantUML plugin - https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml

### Docker

https://hub.docker.com/r/dstockhammer/plantuml - _Not an official PlantUML docker image._

Run the following command to generate images using default options:

```
docker run --rm -v $(pwd):/data dstockhammer/plantuml **/*.puml
```

Run the following command to see full options:

```
docker run --rm dstockhammer/plantuml -h
```

## Generating Documentation

Create `Markdown` from `.puml` files using https://github.com/adrianvlupu/C4-Builder.

Run following command to install `c4builder`:

```
npm i -g c4builder
```

Create `.c4builder` config:

```json
{
	"plantumlVersion": "latest",
	"projectName": "<Name>",
	"homepageName": "Overview",
	"rootFolder": "diagrams",
	"distFolder": "docs",
	"generateMD": true, // automatically generate MD file
	"generatePDF": false,
	"generateCompleteMD": false,
	"generateCompletePDF": false,
	"generateWEB": false,
	"webTheme": "//unpkg.com/docsify/lib/themes/vue.css",
	"supportSearch": "false",
	"repoUrl": "false",
	"docsifyTemplate": "",
	"webPort": "3000",
	"pdfCss": "/opt/homebrew/lib/node_modules/c4builder/pdf.css",
	"includeBreadcrumbs": false,
	"includeLinkToDiagram": false,
	"includeTableOfContents": true, // add table of contents
	"diagramsOnTop": true,
	"embedDiagram": false,
	"excludeOtherFiles": false,
	"generateLocalImages": true, // generate images vs plantuml links
	"plantumlServerUrl": "https://www.plantuml.com/plantuml",
	"diagramFormat": "png",
	"charset": "UTF-8"
}
```

Run following command to generate `Markdown`:

```
cd <config location>
c4builder
```

_Note: when you run `c4builder` it add/updates `checksums` property in the config._
