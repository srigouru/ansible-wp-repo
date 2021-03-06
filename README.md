# Ansible role `wordpress`


An Ansible role for installing Wordpress. Specifically, the responsibilities of this role are to:

- install the EPEL repository and Wordpress dependencies
- install Wordpress
- set up the database and configure Apache
- fetch security keys and salts
- generate `wp-config.php`

## Dependencies

- [bertvv.httpd](https://galaxy.ansible.com/list#/roles/3047)

## Requirements

You need to have a database server set up with a database, user, and password that can is available to this Wordpress instance. You can set it up on the same machine (e.g. using another Ansible role like [bertvv.mariadb](https://github.com/bertvv/ansible-role-mariadb)), but it can also be an existing database on another host.

## Role Variables

| Variable                      | Default     | Comments (type)                                                                                    |
| :---                          | :---        | :---                                                                                               |
| `wordpress_allow_file_mods`   | false       | When `true`, installation of additional themes and plugins through the admin dashboard is allowed |
| `wordpress_automatic_updates` | false       | When `true`, automatic updates are enabled                                                         |
| `wordpress_database_host`     | 'localhost' | The database server.                                                                               |
| `wordpress_database`          | 'wordpress' | The name of the database for Wordpress.                                                            |
| `wordpress_debug`             | false       | When `true`, enables debug mode                                                                    |
| `wordpress_force_ssl`         | false       | When `true`, forces HTTPS on admin pages.                                                          |
| `wordpress_password`          | 'wordpress' | The password of the database user.                                                                 |
| `wordpress_plugins`           | []          | Plugins to be installed. See below.                                                                |
| `wordpress_themes`            | []          | Themes to be installed. See below.                                                                 |
| `wordpress_user`              | 'wordpress' | The name of the database user.                                                                     |

**Remark:** it is **very strongly** suggested to change the default password.

## Plugins and themes

To install plugins and themes (from the Wordpress Plugin and Theme Directory), you need to specify at least the name. Most plugins and themes also have a version, in which case you need to provide it as well. The version number should not be given if the plugins does't have one. An example:

```yaml
wordpress_plugins:
  - name: wp-super-cache
    version: 1.4.5
  - name: jetpack
    version: 3.7.2
  - name: lipsum  # Plugin without a version
wordpress_themes:
  - name: xcel
    version: 1.0.9
```


## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome. The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork. Github can then easily create a PR based on that branch.


## Source Origin:
- [Bert Van Vreckem](https://github.com/bertvv/) 

## License

2-clause BSD license, see [LICENSE.md](LICENSE.md)
