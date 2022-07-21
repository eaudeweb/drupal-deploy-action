# Deploy a release to the server

## Usage

```yml
on: [pull_request]
name: Test 
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:

      - uses: eaudeweb/drupal-deploy-action@v2
        with:
          # The branch, tag or SHA to checkout.
          ref:              test
          # Absolute path where the project root is configured.
          project_dir:      ${{ secrets.TEST_PROJECT_DIR }}
          # Absolute path where the artifacts will be stored.
          artifacts_dir:    ${{ secrets.TEST_ARTIFACTS_DIR }}
          # Name of the release where new release is installed (e.g. release-68cdf63).
          release_id:       ${{ steps.artifact.outputs.base }}
          # Name of the resulted release archive (e.g. release-68cdf63.tar.gz).
          release_filename: ${{ steps.artifact.outputs.filename }}
          # SSH user account.
          ssh_user:         ${{ secrets.TEST_SSH_USER }}
          # SSH host server (IP or public hostname).
          ssh_host:         ${{ secrets.TEST_SSH_HOST }}
          # SSH private key.
          ssh_key:          ${{ secrets.TEST_SSH_KEY }}
          # Check if there are configuration changes in the Drupal database not exported in config. If set to true, the
          # script will fail if there are any changes.
          check_config:     false
          # Create a SQL database backup before doing the deployment (with release filename).
          sql_backup:       false
```
