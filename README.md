# slidev-esp-template

This project is a template for [Slidev](https://github.com/slidevjs/slidev) presentations recommended for use at [Espressif](https://www.espressif.com/).

The template is based on the Slidev [Getting Started](https://sli.dev/guide/) project with the following changes:

- **Theme**: instead of `seriph`, it uses the `default` theme.
- **Addons**: it includes
  - [slidev-addon-sync](https://github.com/Smile-SA/slidev-addon-sync) -- for usage instructions, see [Slide syncing](#slide-syncing)
  - [Poll and Quiz](https://github.com/Smile-SA/slidev-component-poll) -- see a usage example in [slides.md](./slides.md#poll-and-quiz-added-in-slidev-esp-template) > *Poll and Quiz*.
- **Layout**: Espressif logo added.
- **Slide content**: changed or added guidelines in
  - *Themes*
  - *Poll and Quiz*


## Installation and configuration

The instructions below may seem detailed, but that's intentional — the Node.js ecosystem can be unintuitive for those who don’t work with it regularly.

These steps have been tested on Linux. The general approach should be similar on Windows and macOS, but some adjustments may be necessary.
If you run into major issues, feel free to open an issue — we’ll do our best to update the instructions accordingly.

### Software dependencies

Slidev requires `Node.js`, which can be conveniently installed using [nvm](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating):

```sh
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.nvm/nvm.sh
# Install Node.js (LTS version includes npm)
nvm install --lts
# Install pnpm globally (recommended over npm for faster installs and disk efficiency)
npm install -g pnpm
```


### Template setup

To create your presentation:

1. On the GitHub repo page, click **Use this template** in the top-right corner.
    - This creates a new repo under your GitHub account with the contents of `slidev-esp-template`.
2. Clone your new repo:
    ```sh
    git clone https://github.com/YOUR_USERNAME/slidev-esp-template.git
    cd ~/path/to/slidev-esp-template/
    ```
3. Install project dependencies:
    ```sh
    pnpm install
    ```
4. (Optional but recommended) Set up your environment to use Slidev globally:
    ```sh
    # Create a global bin directory and add it to your shell's PATH
    pnpm setup
    # Restart your shell
    # Install the Slidev CLI globally
    pnpm add -g @slidev/cli
    ```
    💡 If you prefer not to install anything globally, you can run Slidev using `pnpm exec slidev`.

## Usage

To start the slide show:

- Run `slidev`
- Visit <http://localhost:3030>

Edit the [slides.md](./slides.md) to see the changes.


## Learn more about Slidev

Slidev has extensive [documentation](https://sli.dev/).

To get started, see:

- [Syntax Guide](https://sli.dev/guide/syntax)
- [Directory Structure](https://sli.dev/custom/directory-structure)
- [User Interface](https://sli.dev/guide/ui)


## Slide syncing

To enable slide syncing, run:

```sh
slidev --remote=<password>
```

This command will return the links for the presenter and attendees.


### Troubleshooting

If slide syncing doesn't work, make sure that:

- The dev server (`slidev --remote`) is running somewhere (usually the presenter's device).
- The presenter is using the presenter link.
- The presenter's and attendee's devices are connected to the same network.
- The device's OS does not block access to the LAN due to the use of VPN clients, etc.
