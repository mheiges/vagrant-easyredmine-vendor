
This Vagrant project is ported from the VMWare image provided by
EasyRedmine. Reference my Nov. 10, 2015 email 'Redmine Installation made
Easy', from "Ondrej, Easy Redmine" <ondrej@mailing.easyredmine.com>

It includes Redmine 3.1.1 pre-installed on Debian 8. See
`README-vendor.md` for details provided by the EasyRedmine vendor. Note
that this is vanilla Redmine, without the EasyRedmine extensions. The
vendor says their extensions are not compatible with Redmine 3.1.1 (as
of November 2015) so it beats me why the vendor is distributing the
VMWare image.

There's probably not much point in this project except to experiment
with migrating our Redmine 2 database to Redmine 3.

The Redmine site is accessible at http://easyredmine.vm.apidb.org/

## Requirements

- Vagrant `landrush` plugin

### Optional

- `scratch/redmine_dump.sql.gz` - a mysql dump of our production
database if you want to play with real data.  _(One of the daily backups
on our production Redmine server is suitable. See
`/var/lib/mysql.backups/daily/redmine/`.)_

- `scratch/easyredmine_package_u2072_d201511101601.zip` - the
installation package provided by EasyRedmine (downloaded from their
customer portal) if you want to play with migrating vanilla Redmine to
EasyRedmine.


## Redmine sample data

To install an empty database, set `do_redmine_db_import` to `False` in
`roles/easyredmine/vars/main.yml`

To import a copy of an existing Redmine database, place a copy of the
MySQL dump file at `scratch/redmine_dump.sql.gz`. _(One of the daily
backups on our production Redmine server is suitable. See
`/var/lib/mysql.backups/daily/redmine/`.)_

Set `do_redmine_db_import` to `True` in `roles/easyredmine/vars/main.yml`
