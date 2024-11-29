# GLTF-GLB Converter

A pure Node.js module for converting between GLTF and GLB formats without any external dependencies.

## Installation

```bash
# Install globally to use CLI commands
npm install -g gltf-glb-converter

# Or install locally in your project
npm install gltf-glb-converter
```

## Usage

### Command Line Interface

After installing globally, you can use the CLI commands:

```bash
# Convert GLTF to GLB
gltf2glb ./input-directory ./output.glb

# Convert GLB to GLTF
glb2gltf ./input.glb ./output-directory
```

### Programmatic Usage

```javascript
const { gltf2glb, glb2gltf } = require('gltf-glb-converter');

// Convert GLTF to GLB
await gltf2glb('./input-directory', './output.glb');

// Convert GLB to GLTF
await glb2gltf('./input.glb', './output-directory');
```

## Features

- Pure Node.js implementation (no dependencies)
- Converts GLTF files and their assets to a single GLB file
- Extracts GLB files into GLTF and associated assets
- Handles binary buffers and embedded images
- Supports both file references and data URIs (base64) in GLTF
- Cross-platform compatible
- Command-line interface
- Programmatic API

## Asset Handling

The converter supports two ways of referencing assets in GLTF files:

1. File References:
```json
{
  "buffers": [
    { "uri": "buffer.bin", "byteLength": 1234 }
  ],
  "images": [
    { "uri": "texture.png" }
  ]
}
```

2. Data URIs (base64):
```json
{
  "buffers": [
    { "uri": "data:application/octet-stream;base64,AAAAAA==", "byteLength": 1234 }
  ],
  "images": [
    { "uri": "data:image/png;base64,iVBORw0KGgo..." }
  ]
}
```

Both formats are automatically detected and properly handled during conversion.

## API

### CLI Commands

#### gltf2glb
```bash
gltf2glb <input-directory> <output-glb-file>
```
- `input-directory`: Directory containing the .gltf file and its assets
- `output-glb-file`: Path where the GLB file should be saved

#### glb2gltf
```bash
glb2gltf <input-glb-file> <output-directory>
```
- `input-glb-file`: Path to the input GLB file
- `output-directory`: Directory where the GLTF and assets should be saved

### Programmatic API

#### gltf2glb(inputDir, outputPath)
- `inputDir`: Directory containing the .gltf file and its assets
- `outputPath`: Path where the GLB file should be saved

#### glb2gltf(inputPath, outputDir)
- `inputPath`: Path to the input GLB file
- `outputDir`: Directory where the GLTF and assets should be saved

## License

MIT
