# Ubuntu Developer Proxy Configurations

A comprehensive guide to configuring proxy settings on Ubuntu for developers. This repository provides step-by-step instructions for various tools and environments, including system-wide settings, the terminal, APT, Git, Docker, and more, to streamline your development workflow behind a proxy.

---

## Table of Contents

1.  [APT (Advanced Package Tool)](#apt)

---

## APT

To configure APT to use a proxy for downloading packages and updates, you need to create a custom configuration file.

1.  Create and open a new configuration file in the `/etc/apt/apt.conf.d/` directory using a text editor like `nano`:

    ```bash
    sudo nano /etc/apt/apt.conf.d/80proxy
    ```
    *(Note: The filename `80proxy` is a convention; any name will work.)*

2.  Add the following lines to the file, replacing `your-proxy-address` and `port` with your actual proxy server's details.

    ```
    Acquire::http::Proxy "http://your-proxy-address:port/";
    Acquire::https::Proxy "https://your-proxy-address:port/";
    Acquire::ftp::Proxy "ftp://your-proxy-address:port/";
    ```

    **Example:** If your proxy is at `http://localhost:8086`, you would write:
    ```
    Acquire::http::Proxy "http://localhost:8086/";
    Acquire::https::Proxy "https://localhost:8086/";
    ```

3.  Save the file and exit the editor (in `nano`, press `Ctrl+X`, then `Y`, then `Enter`).

APT will now use these settings for all future package operations.

### For Proxies with Authentication

If your proxy requires a username and password, include them in the URL like this: