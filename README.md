# curl-with-random-proxy

`curl-with-random-proxy` is a wrapper script for `curl`, designed to automatically select a working SOCKS5 proxy for each HTTP/HTTPS request. The script fetches a list of SOCKS5 proxies, tests their connectivity, and chooses a random working proxy to send the request. If a proxy is non-working, it will try the next one and remove the non-working proxy from the list, continuing the process until a working proxy is found or no more proxies are available in the list.

## Features

- Fetch SOCKS5 proxy list from a configurable source
- Test proxy connectivity before use
- Automatically try the next proxy and remove non-working proxies from the list
- Randomly select a working proxy for each request
- Customizable proxy timeout and list update interval
- Passes all command-line arguments to the underlying `curl` command

## Prerequisites

The script relies on the following command line tools, which are commonly available on most Linux systems:

- curl
- dos2unix
- date
- head
- mkdir
- mktemp
- mv
- stat
- tail
- wc

If any of these tools are missing, you can usually install them using your system's package manager (e.g., `apt`, `yum`, or `pacman`).

## Installation

1. Download the `curl-with-random-proxy` script.
2. Make the script executable with `chmod +x curl-with-random-proxy`.
3. Move the script to a directory in your `$PATH`, e.g., `sudo mv curl-with-random-proxy /usr/local/bin/`.

## Usage

Use the `curl-with-random-proxy` command instead of `curl`:

```sh
curl-with-random-proxy https://ipinfo.tw
```

The script accepts all command-line arguments that curl does, and passes them through to the underlying curl command.

## Customization

You can customize the following variables through environment variables to suit your needs:

- `SOCKS5_PROXY_LIST`: Path to the file containing the list of SOCKS5 proxies. By default, the script uses a file in the `~/.curl-with-random-proxy` directory.
- `SOCKS5_PROXY_SOURCE`: URL of the SOCKS5 proxy list source. Defaults to a GitHub project: [TheSpeedX/SOCKS-List](https://github.com/TheSpeedX/PROXY-List).
- `PROXY_TIMEOUT`: Timeout in seconds for testing proxy connectivity (default: `3`).
- `PROXY_LIST_TTL`: Time in seconds between updates of the proxy list (default: `10800`, i.e., 3 hours).
- `CURL_USER_AGENT`: User agent string for `curl` requests (default: a recent Firefox user agent).

## License

GPL-2.0 (GNU GENERAL PUBLIC LICENSE Version 2)
