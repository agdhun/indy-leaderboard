# Example Leaderboard dApp for utilizing EbakusDB at Ebakus blockchain


## 1. Set the .env variables

You first have to set your wallet info in the [.env](/.env) file, so as all three modules can communicate with the contract. If you don't know how to get the mnemonic or private key, we will generate one for you at step 3, and instruct you to copy the values in the [.env](/.env) file.

## 2. Install the needed packages

```
yarn
```

## 3. Contract build and deploy

```
truffle compile && truffle migrate
```

> If you had to place your keys in the [.env](/.env) file, then re-run this step.

## 4. Start the frontend dApp (read access only)

```
yarn serve
```

> You can access the dApp at `http://localhost:8080`.

## 5. Use an example dApp for utilizing contract (write access)

```
node example_game/index.js
```

> Using the node app (step 3) you can insert the demo content.