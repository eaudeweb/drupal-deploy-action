# Deploy a release to the server

## Usage

```yml
steps:
  - uses: actions/checkout@v3

  - uses: eaudeweb/drupal-install-action@main

  - uses: eaudeweb/drupal-artifact-action@main
    id: artifact

  - uses: eaudeweb/drupal-deploy-action@2.x
    with:
      ssh_user:           ${{ secrets.TEST_SSH_USER }}
      ssh_host:           ${{ secrets.TEST_SSH_HOST }}
      ssh_key:            ${{ secrets.TEST_SSH_KEY }}
      release_id:         ${{ steps.artifact.outputs.base }}
      release_filename:   ${{ steps.artifact.outputs.filename }}
      artifacts_dir:      /var/www/artifacts/www.example.com
      project_dir:        /var/www/html/www.example.com
      settings_file:      /var/www/config/www.example.com/settings.local.php
      env_file:           /var/www/config/www.example.com/.env
      robo_file:          /var/www/config/www.example.com/robo.yml
      public_files_dir:   /var/www/config/www.example.com/files
      private_files_dir:  /var/www/config/www.example.com/private
      database_dump_dir:  /var/www/config/www.example.com/sync
      artifacts_lifespan: 30
```