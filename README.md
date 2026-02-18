# AMAT-Producer-wafer-match-tool
AMAT Producer wafer match tool
Wafer Match Tool v3 (Web Edition)
A web-based visualization utility designed for semiconductor equipment engineers. This tool simulates and calculates wafer notch angles and orientations within Front Interface (FI) modules (FI5.X and FI6.4 standards). It allows for visual verification of wafer paths, notch alignments, and slit valve orientations relative to the transfer robot.

🎯 Key Features
Multi-Standard Support: Supports both FI5.X and FI6.4 equipment modes with specific angle logic for each.

Dynamic Path Visualization: Automatically highlights the transfer path based on selected Cassette, Side, and Target Station.

Real-time Angle Calculation: Calculates the precise notch angle for every station (Cassettes, Load Locks, Alignment, and Process Chambers).

Image Overlay Support:

Upload local wafer images.

Clipboard Support: Paste images (Ctrl+V) directly into the tool.

The tool automatically crops and rotates the uploaded image to match the simulated wafer notch angle.

Interactive Zoom View:

Click on any wafer to open a detailed popup.

Auto-Rotation: The popup rotates the view to match the physical perspective of the station (e.g., Slit Valve orientation for CHA/CHB/CHC).

Visual Indicators: Clearly marks the "SLIT VALVE" location with correctly mirrored text for intuitive verification.

Responsive Design: Implements proportional scaling (ZOOM_FACTOR) to ensure the layout fits perfectly on different screen sizes without distortion.

🚀 Getting Started
Since this is a client-side only application contained within a single HTML file, no installation or server setup is required.

Prerequisites
A modern web browser (Chrome, Edge, Firefox, Safari).

Usage
Clone or Download this repository.

Double-click index.html (or whatever you named the file) to open it in your browser.

📖 User Guide
Configuration: Use the control panel at the top to set your parameters:

Mode: Select between FI5.X or FI6.4 logic.

Cassette: Source cassette (A, B, C, or D).

Side: Robot side (S1 or S2).

Target: Destination station (LL, CHA, CHB, CHC).

Offset: (Optional) Add a rotational offset if necessary.

Load Image:

Click "Upload Image" to select a file, OR

Copy an image to your clipboard and press Ctrl+V on the page.

Analyze:

Observe the highlighted path (White wafers) vs non-path positions (Light Blue).

Red indicators show the calculated Notch Angle.

Zoom & Verify:

Click on any specific wafer (e.g., CHA).

A popup will appear showing the wafer rotated relative to the Slit Valve.

Verify if the physical notch orientation matches the simulation.

🔧 Technical Details
Canvas API: The entire visualization is rendered using the HTML5 Canvas API, allowing for high-performance 2D drawing and matrix transformations.

Matrix Transformations:

ctx.translate, ctx.rotate, and ctx.scale are used extensively to handle the "View Rotation" logic in the popup.

Specifically, ctx.scale(-1, -1) is used to create a vertical flip effect for the "SLIT VALVE" text to mimic specific viewing angles.

Proportional Scaling: The drawLayout function calculates a fitScale based on the window size and a reference dimension (600x750), ensuring the schematic remains centered and proportional.

📐 Logic Overview
The tool calculates angles based on hardcoded rulesets for standard semiconductor platforms. Example logic snippet:

JavaScript
// Example: FI5.X Logic
if (mode === "FI5.X") {
    if (["A", "B"].includes(cassName)) {
        // S1 Side Rules
        rules = (side === "S1") 
            ? {"LL1": 210, "A1": 30, "B1": 300, ...} 
            : {...};
    }
    // ...
}
🤝 Contributing
Contributions are welcome! If you find a bug in the angle logic or want to add support for new module types:

Fork the repository.

Create your feature branch (git checkout -b feature/AmazingFeature).

Commit your changes.

Push to the branch.

Open a Pull Request.

📄 License
Distributed under the MIT License. See LICENSE for more information.

Note: This tool is for simulation and reference purposes. Always verify with actual equipment telemetry when performing critical calibrations.
