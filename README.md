<h1 align="center">
  <img src="https://github.com/projectdiscovery/notify/blob/master/static/notify-logo.png" alt="notify" width="200px"></a>
  <br>
</h1>

<h4 align="center"><a href="https://github.com/projectdiscovery/notify-action">Notify Action</a> makes it easy to orchestrate <a href="https://github.com/projectdiscovery/notify">notify</a> with GitHub Action.</h4>



Example Usage
-----

**GitHub Action running Notify with file**

```yaml
      - name: 🗒 Notify - Keep me updated
        uses: projectdiscovery/notify-action@main
        with:
          data: output.txt
          config: notify-config.yaml
```

**Example workflow** - `.github/workflows/notify.yml`


```yaml
name: 🗒 Notify - Keep me updated

on:
    schedule:
      - cron: '0 0 * * *'
    workflow_dispatch:

jobs:
  notify-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-go@v3
        with:
          go-version: 1.17

      - name: 🗒 Notify - Keep me updated
        uses: projectdiscovery/notify-action@main
        with:
          data: output.txt
          config: notify-config.yaml
```


Available Inputs
------

| Key      | Description                        | Required |
|----------|------------------------------------|----------|
| `data`   | Input file to send with notify     | false    |
| `config` | Config file to use with notify     | false    |
| `flags`  | Additional notify CLI flags to use | false    |
