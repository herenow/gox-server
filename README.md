gox-server
====

[![GitHub release](http://img.shields.io/github/release/tcnksm/gox-server.svg?style=flat-square)][release]
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)][license]
[![Go Documentation](http://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)][godocs]

[release]: https://github.com/tcnksm/gox-server/releases
[license]: https://github.com/tcnksm/gox-server/blob/master/LICENSE
[godocs]: http://godoc.org/github.com/tcnksm/gox-server

Golang cross compile on Heroku.

Just request some golang GitHub repository name, you can download compiled binary for your platform without golang runtime on your local PC. Currently request repository must be `go build`-able. Support platform is Darwin/Linux/Windows, 386/amd64. This is just POC and playing with [Heroku with Docker](https://devcenter.heroku.com/articles/introduction-local-development-with-docker). You should prepare your own build environment. 

## Demo

Demo application is hosted on [https://gox-server.herokuapp.com/](https://gox-server.herokuapp.com/).

For example, if you want [github.com/Soulou/curl-unix-socket](https://github.com/Soulou/curl-unix-socket) compiled binary, 

```bash
$ curl -A "`uname -sp`" https://gox-server.herokuapp.com/Soulou/curl-unix-socket > curl-unix-socket
$ chmod a+x curl-unix-socket
```

Or access from your browser [https://gox-server.herokuapp.com/Soulou/curl-unix-socket](https://gox-server.herokuapp.com/Soulou/curl-unix-socket).

## Usage

To get binary for platform (`uname -sp`) hosted on [github.com/OWNER/REPO](),

```bash
$ curl -A "`uname -sp`" https://gox-server.herokuapp.com/OWNER/REPO > REPO
```

## Development

You can run this on local dev environment. You need to prepare `docker` and [heroku docker plugin](https://devcenter.heroku.com/articles/introduction-local-development-with-docker).

```bash
$ heroku docker:start
```

And just request (e.g., your docker works on `192.168.59.103`),

```bash
$ curl -A "`uname -sp`" http://192.168.59.103:3000/tcnksm/ghr > ghr
```

## Release

You can setup your own build server on Heroku. After create account on Heroku, run below,

```bash
$ heroku create
$ herocku docker:release
```

## Contribution

1. Fork ([https://github.com/tcnksm/gox-server/fork](https://github.com/tcnksm/gox-server/fork))
1. Create a feature branch
1. Commit your changes
1. Rebase your local changes against the master branch
1. Run test suite with the `make test` command and confirm that it passes
1. Run `gofmt -s`
1. Create new Pull Request

## Author

[Taichi Nakashima](https://github.com/tcnksm)
