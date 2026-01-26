# Oh My Memo

This is a personal documentation collection built with Sphinx, containing memos and tutorials on topics such as seismology, programming, and more.

## Table of Contents

- [Links](links/index.md) - Useful links and resources
- [Seismo](seismo/index.md) - Seismology related content
- [Prog](prog/index.md) - Programming related content

## Installation and Building

### Environment Setup

Create the environment using Conda:

```bash
conda env create -f environment.yml
conda activate docs-post
```

### Build Documentation

```bash
make html
```

The built documentation is located in the `build/html/` directory.

### Local Preview

After building, you can preview using Python's HTTP server:

```bash
cd build/html
python -m http.server 8000
```

Then visit `http://localhost:8000` in your browser.

## Homepage

Visit [xumijian.me](https://xumijian.me) for the online version.

## License

[MIT License](LICENSE) (if applicable)

## Contributing

Welcome to submit Issues and Pull Requests.

欢迎提交 Issue 和 Pull Request。