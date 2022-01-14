# get-site-info

This action lets you fetch site data for use in actions

## Usage

Unless a token is specified, the action will make its own. If it needs to do this, you must give it permissions to do so
by giving it `id-token` permissions either to the job or step.
```yaml
permissions:
    contents: read
    id-token: write
```


General usage is as follows:
```yaml
steps:
  - uses: actions/checkout@master

  - name: Get site information
    id: info
    uses: 'apility-ops/get-site-info@main'
    # Token can be set using the with clause, but is not required

- uses: shivammathur/setup-php@v2
    name: Setup PHP
    with:
    php-version: '7.4'
- uses: ramsey/composer-install@v2
    with:
    composer-options: "--ignore-platform-reqs --optimize-autoloader"
    env:
    NETFLEX_PUBLIC_KEY: ${{ steps.info.outputs.publicKey }}
    NETFLEX_PRIVATE_KEY: ${{ steps.info.outputs.privateKey }} 
    # Site keys are used here to ensure composer runs successfully when installing dependencies for laravel projects.
```


## Outputs

* `publicKey` - Site public key
* `privateKey` - Site private key
* `siteAlias` - Site alias