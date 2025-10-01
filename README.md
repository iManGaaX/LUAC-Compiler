# LUAC Compiler v1.0.0 - by iManGaaX

## Program Overview
**LUAC Compiler** is a desktop application, Designed to convert **Lua** files for **Multi Theft Auto: San Andreas (MTA)** into **.luac** files ready for use and distribution. The application support encryption of server backup files instead of file-by-file and provides a drag-and-drop interface for folders and files, options for obfuscation level, debug mode, and exporting the resulting project as a single file or a ZIP archive. It also supports automatic updates via GitHub and notifies the user when a new version is available.

## Key Features
- User-friendly GUI built.
- Support encryption of backup files instead of file-by-file.
- Drag & drop files or folders, or manually select file.
- Convert `.lua` files to `.luac` using an external API endpoint.
- Multiple obfuscation levels: 0 - 3 (3 recommended).
- Toggle Debug Mode on/off (off recommended).
- Automatic modification of `meta.xml` files (convert `.lua` paths to `.luac`, set `cache="false"`, add/update `<min_mta_version>`).
- Progress bar and status updates for each file with retry logic on failures.

## System Requirements
- Operating System: Windows x32 & Windows x64
- Internet connection: required for compilation (uses external endpoint) and for fetching updates from GitHub.

## Usage Guide (User)
1) Open the application.
2) Drag & drop .lua files or folders containing Lua scripts into the Dropzone,
   or click the Dropzone to select file manually.
3) After adding files, you'll see a list of items (files and folders). You can remove
   any item by clicking the "×" button next to it.
4) Choose the obfuscation level:
   - 0: None
   - 1: Some
   - 2: More
   - 3: Highest (recommended)
5) Choose Debug Mode:
   - 0: Off (recommended)
   - 1: On
6) Click "Start Compile" to begin the conversion.
7) During processing, a progress bar shows completion percentage, and current file status is displayed.
8) After conversion:
   - If there is only one file, it will download directly as .luac.
   - If multiple files exist, a ZIP archive named "Compiled Project.zip" will be generated
     containing all converted files, with updated meta.xml files.

## Quick Examples
- Single file conversion:
  input: script.lua
  output: script.luac

- Full project with multiple folders:
  input: folder-with-scripts/ (Lua files + meta.xml)
  output: Compiled Project.zip
    - Contains: all .luac files, and meta.xml files updated with correct paths and min_mta_version.

## Technical Notes
- Conversion Endpoint: App sends files to https://luac.mtasa.com/index.php via POST (FormData) with fields: luasource, compile, debug, obfuscate. Internet required.
- Retry Logic: Each file attempts conversion up to 3 times (initial + 2 retries) before skipping.

- meta.xml Modification:
Replace .lua with .luac in src attributes.
Add or enforce cache="false".
Add/update <min_mta_version server="X" client="X" /> based on obfuscation level.

- Progress & ETA: Estimated time remaining based on current processing speed (approximate).

## Security & Privacy
- Files are sent temporarily to the endpoint for conversion; not stored permanently.
- Sensitive code should be handled with care. Consider local conversion if privacy is critical.
- Do not share private scripts with untrusted endpoints.

## Contact & Support
- Discord: imangaax
- GitHub Issues: https://github.com/iManGaaX/LUAC-Compiler/issues

## Credits
- LUAC Compiler © iManGaaX. All rights reserved.
- Thank you for using the application. For bugs or suggestions, Contact via Discord or report via GitHub Issues.
