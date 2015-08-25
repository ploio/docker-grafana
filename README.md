# Portefaix Grafana

![logo](http://pkgs.alpinelinux.org/assets/alpinelinux-logo.svg)

[Alpine Linux][] is a Linux distribution built around musl libc and BusyBox.
This image is based on the official Alpine Linux.

[Grafana][] is an open source, feature rich metrics dashboard and graph editor for
Graphite, InfluxDB & OpenTSDB

Port exported is : `3000`

Volumes exported are : `/var/lib/grafana` and `/var/log/grafana`.

## Usage

    $ docker run --rm=true -it -p 3000:3000 portefaix/grafana

## Supported tags

- `2.0.2`

## License

See [LICENSE](LICENSE) for the complete license.


## Changelog

A [ChangeLog.md](ChangeLog.md) is available.


## Contact

Nicolas Lamirault <nicolas.lamirault@gmail.com>


[Alpine Linux]: http://www.alpinelinux.org

[Grafana]: http://grafana.org/
