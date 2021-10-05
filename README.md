# ICPunks

ICPunks is a project to bring an analogue ERC-721 to Dfinity in order to faciliate creation of NFTs. This repository introduces NFT canisters by showing an implementation - ICPunks - a collection of 10,000 Dfinity punks, which will be available for free to claim by community.

In the current version 0.0.1, you’ll be able to compile the local copy of ICPunks together with Dfinity network and frontend running locally. Follow setup instructions below to run it.

This project is sponsored by the Dfinity Developer Grant Programme. 

![Screen after successful deployment, v.0.0.1](https://user-images.githubusercontent.com/22591201/122807088-6e8f2100-d2cb-11eb-8518-5eb236d27c83.png)

## Installation

### Prerequisites

- [Internet Computer SDK] version 0.7.2 (https://sdk.dfinity.org)
- [Node.js](https://nodejs.org), version >= 12
- [Yarn](https://nodejs.org)
- [Python](https://www.python.org)
- [Vessel@0.6.0](https://github.com/dfinity/vessel/releases/tag/v0.6.0)
- If you're using Ubuntu, ensure that vessel and dfx are installed for superuser too. (ie `sudo which dfx` and `sudo which vessel` should work)
- If vessel is not installed, use `./scripts/vessel-install.sh` or
- Get it from https://github.com/dfinity/vessel/releases and put it in `/usr/local/bin` and do a `sudo chmod +x` on it

## Setup


Having dfx version 0.7.2 is important, it's an older version:

```shell
$ DFX_VERSION=0.7.2 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"
$ dfx --version # check that version is 0.7.2
```

The first step to setup ICPunks locally is to clone this git repository:

```bash
$ git clone git@github.com:stopak/ICPunks.git
$ cd ICPunks

```

If you don't have vessel yet you can install it by running an install script included in this project:

```shell

# Install vessel
$ ./scripts/vessel-install.sh # This script gives error on ubuntu

```

This script does work on ubuntu

In case it doesn't work: https://github.com/dfinity/vessel/releases 
and put it in `/usr/local/bin` and do a `sudo chmod +x` on it

Double-check you have [vessel](https://github.com/dfinity/vessel) installed at version 0.6.*, then clone this repository and navigate to the `ICPunks` directory

```shell

$ vessel --version
# vessel 0.6.0

```

Install all dependencies for UI

```shell
yarn # <- This installs packages from the lockfile for consistency
npm install # not sure if this is needed
```

Start a local Internet Computer replica.

```shell
$ dfx start --clean --background
```

Execute the following commands in another terminal tab in the same directory. (If you want to use internet-identity, skip this instruction and go to How to install local identity)

```shell
$ dfx deploy # This may take some time
```

This will deploy a local canister called `icpunks_ui`. To open the front-end, get the asset canister id by running `dfx canister id icpunks_assets`. Then open your browser, and navigate to `http://<icpunks_assets-canister-id>.localhost:8000`.

## Frontend Development

To run a development server with fast refreshing and hot-reloading, you can use this command in the app's root directory:

```shell
$ sudo yarn run start
```

Your default browser will open (or focus) a tab at `localhost:3000`.

Now you can make changes to any frontend code and see instant updates, in many cases not even requiring a page refresh, so UI state is preserved between changes. Occasionally adding a CSS rule won't trigger an update, and the user has to manually refresh to see those changes.
