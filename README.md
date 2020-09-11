# Code sign a file

This action signs `.nupkg` files and files that are supported by `signtool.exe` with a code signing certificate. This action only works on Windows and that means it should run on `windows-latest`.

This actions requires `signtool.exe` to be in the `PATH`.
Use the elprans/gha-setup-vcpp-build-tools action or similar to ensure this.

## Inputs

### `certificate`

**Required** The base64 encoded certificate.

### `certificate-password`

The password to use for password-protected certificates.

### `folder`

**Required** The folder that contains the libraries to sign.

### `recursive`

**Optional** Recursively search for DLL files.

## Example usage

```
runs-on: windows-latest
steps:
  uses: elprans/gha-win-code-sign@v1
  with:
    certificate: '${{ secrets.CERTIFICATE }}'
    certificate-password: '${{ secrets.CERTIFICATE_PASSWORD }}'
    folder: 'files'
    recursive: true
```
