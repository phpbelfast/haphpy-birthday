![haphpy-birthday](https://cloud.githubusercontent.com/assets/5421942/8129742/720530c2-110c-11e5-870c-1c293960d87a.png)

HaPHPy Birthday is about creating a community video celebrating 20 years of the PHP language and its users involvement.

It aims at gathering a maximun of videos or pictures from the community in order to express the gratefulness of worldwide users to the PHP community in a short movie.

## Requirements

* Vagrant
* Vagrant plugin landrush or host manager

## Install

You need landrush to be installed.

```shell
vagrant up
```

In your guest machine run the following command:
```shell
composer install
```

## Usage

Accessing the web pages

http://haphpy-birthday.dev

## Database

* root password: __afuprocks__
* database: __haphpy__
* user: __afup__
* password: __afup__


## Generating fake contributions for development

Checkout the `dev/generate-contributions` branch in your repository.
```shell
git checkout dev/generate-contributions
```

In the guest machine, move to /vagrant directory then run the following command
```shell
php app/console haphpy:contributions:generate <quantity>
```
the optional `quantity` parameter can be set up to 768. It defaults to 100.

> :warning: Currently, the command does not clean either the database or the file system from old contributions.

> Here are the commands to run in your guest machine:
```shell
rm -rf /var/haphpy/contributions/*/*
```
And for the database
```shell
mysql -u afup -p -e 'DELETE FROM contribution' haphpy
```
password: __afup__

## Language

The only page where the locale is not enforced is on the `/` URL. When requested, that URL will try to find the best language available and redirect to `/{locale}/`.

The fallback locale is `en` (english), as this site is intended to gather PHP users from all around the world.

To add a supported locale:
* change the `accepted_languages` value in your `parameters.yml(.dist)`
* supply the correct localized files for entries located in `@AppBundle/Resources/translations`

## Contributing

Before commiting, be sure to run your tests:

```shell
bin/phpunit -v -c app/ src
```

and to check your Coding Standards:

```shell
bin/coke
```
