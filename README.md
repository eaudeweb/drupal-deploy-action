# Deploy a release to the server

## Usage

```yml
on: [pull_request]
name: Test 
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:

      - uses: cristiroma/drupal-deploy-action@main
        with:
          project_dir:      ${{ secrets.TEST_PROJECT_DIR }}
          release_id:       ${{ steps.artifact.outputs.base }}
          release_filename: ${{ steps.artifact.outputs.filename }}
          ssh_user:         ${{ secrets.TEST_SSH_USER }}
          ssh_host:         ${{ secrets.TEST_SSH_HOST }}
          ssh_key:          ${{ secrets.TEST_SSH_KEY }}
```


## Inputs

- `project_dir`      - Absolute path where the project root is configured (where live symlink exists)
- `release_id`       - Name of the release where new release is installed (e.g. release-68cdf63)
- `release_filename` - Name of the resulted release archive (e.g. release-68cdf63.tar.gz)
- `ssh_user`         - SSH user account
- `ssh_host`         - SSH host server (IP or public hostname)
- `ssh_key`          - SSH private key
