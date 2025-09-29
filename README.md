# Any-to-Text File Converter

A simple yet powerful Python script to convert files into a `.txt` format by copying and renaming them. This is particularly useful for preparing entire codebases or directories of files for analysis by Large Language Models (LLMs) or for easy viewing in any standard text editor.

-----

## ✨ Features

  - **Two Operational Modes**:
      - **Copy Mode (Default & Safest)**: Copies files from a source directory to a specified output directory, preserving the original files.
      - **Rename In-Place Mode**: Renames files directly within the source directory. **Use with caution\!**
  - **Recursive Processing**: Option to process files within all subdirectories of the target folder.
  - **Powerful Filtering**: Precisely control which files are processed using both **inclusion** (`included_extensions`) and **exclusion** (`excluded_extensions`) lists. You can easily skip entire folders (e.g., `.git`, `venv`) as well.
  - **User-Friendly Output**: Clear and informative console logs show the script's progress, including which files are processed and a final summary.
  - **No Dependencies**: Runs using standard Python libraries, requiring no external packages.
  - **Cross-Platform**: Works on Windows, macOS, and Linux.

-----

## 🚀 How to Use

### 1\. Prerequisites

  - **Python 3.x** must be installed on your system.

### 2\. Configuration ⚙️

Open the script (`.py` file) in an editor and modify the configuration section at the top.

```python
# ==============================================================================
# CONFIGURATION - CHANGE THESE VALUES
# ==============================================================================

# 1. The full path to the folder you want to process.
#    On Windows: r"C:\Users\YourUser\Documents\MyProject"
#    On macOS/Linux: "/home/youruser/documents/my_project"
target_folder = r"C:\path\to\your\source_folder" # <--- SET YOUR SOURCE FOLDER

# 2. The path where the converted .txt files will be saved.
#    ✨ Using an output folder is the SAFEST option (Copy Mode).
#    ⚠️ If this is set to None, the script will rename original files IN-PLACE.
#    Example: r"C:\path\to\your\output_folder"
output_folder = r"C:\path\to\your\output_folder" # <--- SET YOUR OUTPUT FOLDER

# 3. Set to True to process files in all subfolders.
include_subfolders = True

# 4. List of file extensions to INCLUDE (wildcard supported).
#    Only files matching these patterns will be considered.
included_extensions = ["*.py", "*.js", "*.html", "*.css", "*.md", "*.json"]

# 5. List of file extensions to EXCLUDE from conversion (wildcard supported).
excluded_extensions = ["*.wav", "*.mp4", "*.exe", "*.jpg", "*.png", "*.zip"]

# 6. List of folder names to completely skip.
excluded_folders = ["venv", ".git", "node_modules", "__pycache__", "build", ".idea"]
```

#### **Key Settings Explained:**

  - `target_folder`: The source folder containing the files you want to convert.
  - `output_folder`:
      - Provide a path here to use the safe **Copy Mode**. The script will create this folder if it doesn't exist and replicate the source folder's structure inside it.
      - Set this to `None` to activate the **Rename In-Place Mode**. This will permanently alter the filenames in your `target_folder`.
  - `include_subfolders`: Set to `True` to go through all sub-folders; `False` to only process files in the top level of `target_folder`.
  - `included_extensions`: A list of file patterns to **include**. Only files matching one of these patterns will be considered. To consider all files (before exclusions), you can set this to `["*"]`.
  - `excluded_extensions`: A list of file patterns to **ignore**. This filter runs *after* the inclusion check.
  - `excluded_folders`: A list of folder names to ignore entirely.

### 3\. Run the Script

Save your configuration changes and execute the script from your terminal.

```bash
# If you saved the script as a .py file
python your_script_name.py
```

-----

## 📋 Example Output

When running in **Copy Mode**, the output will look like this:

```
🚀 Starting process in 'Copy Mode'.
   Source: 'F:\OneDrive - Green Energy\Desktop\samples\Flutter'
   Destination: 'F:\OneDrive - Green Energy\Desktop\samples\Flutter\texts'
--------------------------------------------------
✅ Copied: 'main.dart' -> 'main.dart.txt'
✅ Copied: 'pubspec.yaml' -> 'pubspec.yaml.txt'
✅ Copied: 'README.md' -> 'README.md.txt'
✅ Copied: 'app_config.json' -> 'app_config.json.txt'
--------------------------------------------------
🎉 Process Complete!
   - Files Processed: 4
   - Files Skipped (due to filters): 52
   - Warnings/Errors: 0
```

-----

## ⚠️ Important Notes

  - The safest way to use this script is by specifying an `output_folder`. This ensures your original files are never modified.
  - The "Rename In-Place" mode (`output_folder = None`) is a destructive operation. Please be sure you have a backup of your files before using it.

-----

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
