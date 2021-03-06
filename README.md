# OmniFocus Backup Reader

This is a work in progress and will be improved as I improve Intercessor.

This class reads an OmniFocus backup file (from File->Export->File Format->Backup Document (Omnifocus)), and provides access to folders, projects, tasks, and contexts with `TodoMove\Intercessor` classes, which provides a nice fluent interface, and will allow the items to be transformed and exported to different services if needed.

All classes returned are from [TodoMove\Intercessor](https://github.com/todomove/intercessor)

## Installation

`composer require todomove/omnifocus`

## Basic Class Usage

`composer install`

```php
require __DIR__ . '/vendor/autoload.php';
use TodoMove\Service\Omnifocus\Reader;
 
$omnifocus = OmnifocusReader::loadBackup($pathToZipFile);

$tags = $reader->tags(); // Array of your Omnifocus contexts, converted to `TodoMove\Intercessor\Tag`
$folders = $reader->folders(); // Array of `TodoMove\Intercessor\ProjectFolder`
$projects = $reader->projects(); // Array of `TodoMove\Intercessor\Project`
$tasks = $reader->tasks(); // Array of `TodoMove\Intercessor\Task`
```


## Example script usage

`php run.php [path to backup.zip]`

## Notes

* The OmniFocus backup process (File->Export->File Format->Backup Document(OmniFocus)) produces a .zip file with a `contents.xml` which lists all of your folders, projects, contexts and tasks.
* Doesn't support specific week day repeats