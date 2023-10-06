# Blender Addon Build Action

This GitHub action automates the build process for Blender add-ons, producing a `.zip` artifact which can be installed into Blender.

## Author

This action was created by Andreas Gajdosik and [BlenderKit](https://github.com/BlenderKit).

## Description

The **Blender Addon Build** action allows for the automatic building of Blender add-ons.
At the end of the process, the action stores the built add-on as a `.zip` artifact.

## Inputs

### `name`

**Description**: Name of the add-on. This is used for naming the build.  
**Default**: '' (empty string)

### `name-suffix`

**Description**: Specifies the suffix for the build name.  
- **none**: Results in `name.zip`
- **commit-hash**: Results in `name-abc123.zip`
- **PR-time**: Results in `name-PR123-date_time.zip`  
**Default**: 'none'

### `build-command`

**Description**: Command used to build the add-on.  
**Default**: '' (empty string)

### `build-location`

**Description**: Path to the directory which will be zipped up to create the artifact.  
**Default**: './' (current directory)

### `do-checkout`

**Description**: Determines whether the action should checkout the repository.  
**Choices**: 'true', 'false'  
**Default**: 'true'

If you need to checkout the repository before and do same changes, select false so the action does not checkout again and overwrite the files.

### `exclude-files`

**Description**: A list of file paths, relative to `build-location`, to exclude from the build. Use a semicolon as a separator, e.g., `"file1;dir/file2;dir2/file3"`.  
**Default**: '.git'

If your repository contains files and/or directories which should not be included in the build, you can specify them here, e.g., `.git;docs;README.md;tests;.github`.

## Example Usage

```yaml
- name: Build Blender Addon
  uses: BlenderKit/blender-addon-build-action@v1
  with:
    name: 'MyAddon'
    name-suffix: 'commit-hash'
    build-command: 'make build'
    build-location: './build'
    do-checkout: 'true'
    exclude-files: '.git;.github;.gitignore'
```

## Support

For support, issues, or feedback, please visit the [repository](https://github.com/BlenderKit/blender-addon-build-action) and create an issue or a pull request.

