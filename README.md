# training-nft-4

Training n°4 for NFT marketplace

![https://france-vins.eu/wp-content/uploads/2018/10/les-meilleures-caves-%C3%A0-vin-image.jpg](https://france-vins.eu/wp-content/uploads/2018/10/les-meilleures-caves-%C3%A0-vin-image.jpg)

We finish by using multi asset template.

- you have unlimited NFT collections
- you have unlimited quantity of items in each collection

To resume, you are producting any quantity of wine bottles on n collections

# :arrow_forward: Go forward

Keep your code from previous training or get the solution [here](https://github.com/marigold-dev/training-nft-3/tree/main/solution)

> If you clone/fork a repo, rebuild in local

```bash
npm i
cd ./app
yarn install
cd ..
```

# :scroll: Smart contract

## Do breaking changes on nft template to fit with the new library

Point to the new template changing the first import line to

```jsligo
#import "@ligo/fa/lib/fa2/asset/single_asset.mligo" "SINGLEASSET"
```

It means you will change the namespace from `NFT` to `SINGLEASSET` everywhere (like this you are sure to use the correct library)

Change the storage definition

```jsligo

```

Compile again and deploy to ghostnet

```bash
TAQ_LIGO_IMAGE=ligolang/ligo:0.56.0 taq compile nft.jsligo
taq deploy nft.tz -e "testing"
```

```logs
┌──────────┬──────────────────────────────────────┬───────┬──────────────────┬────────────────────────────────┐
│ Contract │ Address                              │ Alias │ Balance In Mutez │ Destination                    │
├──────────┼──────────────────────────────────────┼───────┼──────────────────┼────────────────────────────────┤
│ nft.tz   │ KT1QyJW133XNM5xyMixG1LRk17ComsrdNnsA │ nft   │ 0                │ https://ghostnet.ecadinfra.com │
└──────────┴──────────────────────────────────────┴───────┴──────────────────┴────────────────────────────────┘
```

:tada: Hooray ! We have finished the backend :tada:

# :performing_arts: NFT Marketplace front

Generate Typescript classes and go to the frontend to run the server

```bash
taq generate types ./app/src
cd ./app
yarn install
yarn run start
```

## Update in `App.tsx`

We just need to fetch the token_id == 0.
Replace the function `refreshUserContextOnPageReload` by

```typescript

```

## Let's play

1. Connect with your wallet an choose `alice` account (or one of the administrators you set on the smart contract earlier). You are redirected to the Administration /mint page as there is no nft minted yet
2. Enter these values on the form for example :

- name : Saint Emilion - Franc la Rose
- symbol : SEMIL
- description : Grand cru 2007
- quantity : 1000

3. Click on `Upload an image` an select a bottle picture on your computer
4. Click on Mint button

Your picture will be pushed to IPFS and will display, then you are asked to sign the mint operation

- Confirm operation
- Wait less than 1 minutes until you get the confirmation notification, the page will refresh automatically

Now you can see the `Trading` menu and the `Bottle offers` sub menu

Click on the sub-menu entry

You are owner of this bottle so you can make an offer on it

- Enter a quantity
- Enter a price offer
- Click on `SELL` button
- Wait a bit for the confirmation, then it refreshes and you have an offer attached to your NFT

For buying,

- Disconnect from your user and connect with another account (who has enough XTZ to buy at least 1 bottle)
- The logged buyer can see that alice is selling some bottles from the unique collection
- Buy some bottles while clicking on `BUY` button
- Wait for the confirmation, then the offer is updated on the market (depending how many bottle you bought)
- Click on `bottle offers` sub menu
- You are now the owner of some bottles, you can resell a part of it at your own price, etc ...

For adding more collections, go to the Mint page and repeat the process

# :palm_tree: Conclusion :sun_with_face:

You are able to play with an any NFT template from the ligo library.

Congratulations !

//TODO FA2.1 ???

//TODO pictures to include everywhere
