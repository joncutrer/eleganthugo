# Elegant Hugo - A Bootstrap 4 variant of Beautiful Hugo which is a port of the Beautiful Jekyll Theme

The goal of this theme is to match the layout and style of Beautiful Hugo using Bootstrap 4.

> eleganthugo is currently in development while I convert all styling from bootstrap 3 to bootstrap 4. 

![Elegant Hugo Theme Screenshot](https://github.com/joncutrer/eleganthugo/blob/master/images/screenshot.png)

## Installation

    $ mkdir themes
    $ cd themes
    $ git clone https://github.com/joncutrer/eleganthugo.git eleganthugo

See [the Hugo documentation](http://gohugo.io/themes/installing/) for more information.

## Extra Features

### Responsive

This theme is designed to look great on both large-screen and small-screen (mobile) devices.

### Syntax highlighting

This theme has support for either Hugo's lightning fast Chroma, or both server side and client side highlighting.

#### Chroma

To enable Chroma, add the following to your site parameters:

```
pygmentsCodeFences = true
pygmentsUseClasses = true
[Params]
    UseChroma = true
```

Then, you can use a different style by running:

```
hugo gen chromastyles --style=manni > static/css/syntax.css
```

See [the Hugo docs for more](https://gohugo.io/content-management/syntax-highlighting/).

#### Server side syntax highlighting

Use the `highlight` shortcode (with Pygments),
see [the Hugo documentation](http://gohugo.io/extras/highlighting/) for more information.

To use this feature install Pygments (`pip install Pygments`) and add

```
pygmentsUseClasses = true
pygmentsUseClassic = true
```

to your `config.toml`.

#### Client side syntax highlighting

Use triple backticks ( ``` ) or triple tilde ( ~~~ ) around code blocks.

Client side highlighting does not require pygments to be installed. This currently is only active if you have not selected Chroma, because they don't play well together.

### Disqus support

To use this feature, uncomment and fill out the `disqusShortname` parameter in `config.toml`.

### Staticman support

Add *staticman* configuration section in `config.toml` or `config.yaml`

Sample `config.yaml` configuration

```
  staticman:
    api: https://api.staticman.net/v2/entry/<USERNAME>/<REPOSITORY-BLOGNAME>/master/comments
    pulls: https://github.com/<USERNAME>/<REPOSITORY-BLOGNAME>/pulls
    recaptcha:
      sitekey: "6LeGeTgUAAAAAAqVrfTwox1kJQFdWl-mLzKasV0v"
      secret: "hsGjWtWHR4HK4pT7cUsWTArJdZDxxE2pkdg/ArwCguqYQrhuubjj3RS9C5qa8xu4cx/Y9EwHwAMEeXPCZbLR9eW1K9LshissvNcYFfC/b8KKb4deH4V1+oqJEk/JcoK6jp6Rr2nZV4rjDP9M7nunC3WR5UGwMIYb8kKhur9pAic="
```

You must also configure the `staticman.yml` in you blog website.

```
comments:
  allowedFields: ["name", "email", "website", "comment"]
  branch            : "master"
  commitMessage     : "New comment in {options.slug}"
  path: "data/comments/{options.slug}"
  filename          : "comment-{@timestamp}"
  format            : "yaml"
  moderation        : true
  requiredFields    : ['name', 'email', 'comment']
  transforms:
    email           : md5
  generatedFields:
    date:
      type          : "date"
      options:
        format      : "iso8601"
  reCaptcha:
    enabled: true
    siteKey: "6LeGeTgUAAAAAAqVrfTwox1kJQFdWl-mLzKasV0v"
    secret: "hsGjWtWHR4HK4pT7cUsWTArJdZDxxE2pkdg/ArwCguqYQrhuubjj3RS9C5qa8xu4cx/Y9EwHwAMEeXPCZbLR9eW1K9LshissvNcYFfC/b8KKb4deH4V1+oqJEk/JcoK6jp6Rr2nZV4rjDP9M7nunC3WR5UGwMIYb8kKhur9pAic="
```



### Google Analytics

To add Google Analytics, simply sign up to [Google Analytics](http://www.google.com/analytics/) to obtain your Google Tracking ID, and add this tracking ID to the `googleAnalytics` parameter in `config.toml`.

### Commit SHA on the footer

If the source of your site is in a Git repo, the SHA corresponding to the commit the site is built from can be shown on the footer. To do so, two environment variables have to be set (`GIT_COMMIT_SHA` and `GIT_COMMIT_SHA_SHORT`) and parameter `commit` has to be defined in the config file:

```
[Params]
  commit = "https://github.com/<username>/<siterepo>/tree/"
```
  
This can be achieved by running the next command prior to calling Hugo:

```
  GIT_COMMIT_SHA=`git rev-parse --verify HEAD` GIT_COMMIT_SHA_SHORT=`git rev-parse --short HEAD`
```
  
See at [xor-gate/xor-gate.org](https://github.com/xor-gate/xor-gate.org) an example of how to add it to a continuous integration system.
  
## About

This Hugo Theme is a fork of [Beautiful Hugo](https://github.com/halogenica/beautifulhugo) by [Michael Romero](http://halogenica.net/) which is a port of the Jekyll theme [Beautiful Jekyll](http://deanattali.com/beautiful-jekyll/) by [Dean Attali](http://deanattali.com/aboutme#contact). It supports most of the features of the original theme.

## License

MIT Licensed, see [LICENSE](https://github.com/halogenica/Hugo-BeautifulHugo/blob/master/LICENSE).
