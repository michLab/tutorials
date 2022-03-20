# Notes on Visual Studio Code

## Create multi-root workspace

Just follow [tutorial](https://code.visualstudio.com/docs/editor/multi-root-workspaces).

Or simply put the _folders_ section into file_name.code-workspace file:
```json
{
        "folders": [
        {
            "path": "path-to-project-1"
        },
        {
            "path": "path-to-project-2"
        },
        {
            "path": "path-to-project-3"
        }
    ],

}
```
