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


## Required software

Slidev requires `Node.js` and `npm`. To install these packages, consider using [nvm](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating).


## Usage

To create your own project:

1. On the GitHub repo page, click **Use this template** in the top right corner.
    - This creates a new repo under your GitHub account with the copy of `slidev-esp-template`.
2. Clone the new repo.

To start the slide show:

- `pnpm install`
- `pnpm dev`
- visit <http://localhost:3030>

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
