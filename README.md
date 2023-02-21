# ChatGPT prompt to create an array in Powershell containing filenames based on a list.

## Prompt
>Can you provide me with a PowerShell array called $newFileNames containing the updated file names with .mp4 extension and spaces for the following list
>
> Introduction  
> Getting Started  
> Installation


## Result
```powershell
$newFileNames = @(
    "Introduction.mp4",
    "Getting Started.mp4",
    "Installation.mp4"
)
```

## Reason for use
This complements the following powershell script which will rename files which are in the form of filename-1, filename-2, filename-3... in to the file names of $newFileNames

```powershell

# Set the directory path
$dirPath = "C:\temp"

# Get the list of files in the directory
$files = Get-ChildItem $dirPath | Sort-Object {[int]($_.BaseName -split '-')[-1]}

# Set the new file names in the correct order
$newFileNames = @(
    "Introduction.mp4",
    "Getting Started.mp4",
    "Installation.mp4"
)

# Loop through each file and rename it using the corresponding new file name
for ($i = 0; $i -lt $files.Count; $i++) {
    $file = $files[$i]
    $newFileName = $newFileNames[$i]
    Rename-Item $file.FullName -NewName $newFileName
}
```
