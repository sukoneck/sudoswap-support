<!-- 
  when updating: 
    1. Add the answer to the relevant FAQ section
    2. Add the heading to the Contents section with a link to the header
 -->

# Contents

## [How-to FAQ](#how-to-faq)
- [How do I add (W)ETH to a swap?](#how-do-i-add-weth-to-a-swap) 

## [Troubleshooting FAQ](#troubleshooting-faq)
- [Asset approvals](#asset-approvals)
- [Transfer failed](#transfer-failed)

## [How sudoswap.xyz works FAQ](#how-sudoswapxyz-works-faq)
- [At what cost?](#at-what-cost)
- [Are my assets locked once I create a swap?](#are-my-assets-locked-once-I-create-a-swap)
- [What happens if my parter accepts a swap but I don't have the assets any more?](#what-happens-if-my-parter-accepts-a-swap-but-i-dont-have-the-assets-any-more)
- [Do I have to approve all of my assets?](#do-I-have-to-approve-all-of-my-assets)
- [Why can't I swap ETH?](#why-cant-i-swap-eth)
- [Which networks are supported?](#which-networks-are-supported)

<!-- 
  "how-to" is for when you want to know how to do something 
 -->

# How-to FAQ

## How do I add (W)ETH to a swap? 
1. We can only swap ERC20, ERC721, and ERC1155. So, we swap [WETH](https://etherscan.io/token/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2) which is ERC20, never pure ETH. [More info](#why-cant-i-swap-eth).
2. When creating a swap, select the `+ add assets` button.
3. Select the `Form` button, fill it out, then submit:
    ```
    Asset Type    = ERC20
    Asset Address = 0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2
    Amount        = <your-amount>
    ```

<!-- 
  "troubleshooting" is for when you run into an issue 
 -->

# Troubleshooting FAQ

## Asset approvals
You attempt to create a swap but the `create swap` button is greyed out or you are receiving this message:
```
Please approve all offered assets first.
```
There are two reasons you would get this message:
1. You have not approved one or more of the assets you are attempting to swap. So, make sure that each of the assets you are offering in the swap are approved.
2. You submitted the approval transaction, but the approval transaction itself has not completed yet. So, make sure that all of your approval transactions have completed successfully.   

## Transfer failed
You attempt to accept a swap but are receiving this message:
```
Error: execution reverted: TRANSFER_FAILED
```
Here are common reasons that a swap fails. Ask yourself/partner:

### Do you still own all of the assets? 
- One or both people may have already sent one of the assets somewhere else. Your error message may contain `"code": 3` which about the assets not being available in either wallet (no or not enough WETH / ERC not in the wallet). So, the swap is no longer able to be filled. 
- You may either leave the swap open indefinitely or cancel it. 

### Are your approval transactions complete? 
- An approval transaction may still be in progress and hasn't successfully completed yet for one or more of the assets. So, the swap is not yet able to complete the swap. 
- You may confirm the transaction status(es) in Etherscan.  

### Are all of the assets encoded correctly? 
- One or more of the assets are incorrectly assigned the wrong ERC. E.g. an ERC1155 being assigned as an ERC721. 
- You may confirm the asset types in asset's contract on Etherscan or in the details field in an NFT marketplace. 

```
NOTE: If none of these are causing your issue, then there may be an issue with one of the contract for one of the assets. You may try swapping different assets to confirm. 
```

## Transaction dropped
You attempt a transaction to either approve assets or accept a swap and are notified that your transaction was `Dropped`. The most common reason a transaction is dropped is because the price for gas was too low that the Ethereum validation notes dropped the transaction. You may resubmit your transaction with an [appropriate](etherscan.io/gastracker) gas price. 


<!-- 
  "how it works" is for when you want to understand the service  
 -->

# How sudoswap.xyz works FAQ

## At what cost?
No fees, yes gas. There are NO fees; Sudoswap is free. However, there are unavoidable transactions that allow the swap to happen. These required transactions are: 

1. Both partners have to approve their [assets](#do-I-have-to-approve-all-of-my-assets) to swap. 
2. The swap accepter has to accept. 
3. The swap creator has to pay to cancel it (if they want to).

The gas price is up to you as always, but in general the computational cost of each of these transactions is pretty low. 

## Are my assets locked once I create a swap?
No. Assets never leave your wallet until someone accepts the swap.

To recap, so far: 
1. You approved for your assets to be swapped *only if that swap is accepted*.
2. You created a swap agreement.
3. You are waiting for your partner to approve their assets to be swapped and then for your partner to accept the swap.

So, the assets have not left your wallet. There is no hold or lock on your assets. There are only the approvals and swap agreement you created. 

## What happens if my parter accepts a swap but I don't have the assets any more?
The swap transaction fails. 

To recap, so far: 
1. You approved for your assets to be swapped *only if that swap is accepted*.
2. You created a swap agreement.
3. `ISSUE` You sold one or more of the assets in the swap agreement.
4. Your partner approved for their assets to be swapped.
5. Your partner accepted the swap.

So, since the swap cannot be fulfilled (due to step #3), the swap transaction will fail. 

## Do I have to approve all of my assets?
### Short answer
Yes. If you or your partner are swapping multiple items you both need to approve each of them. There is unfortunately no way around this. 

### Long answer
In the ethereum world, approving an asset means you can give some program (i.e. smart contract) permission to move your asset. For example, when trading a token on uniswap the contract has to be able to take tokens out (of your address) and give you eth. In the same way, the 0x contracts that power sudoswap need to have your permission to take NFTs/tokens out (of your address) and give you the desired swap items in return. 

Each token has its own contract so for every new asset you need a new approval transaction. For NFTs we can cheat a little bit using a function called `setApprovalForAll` which allows you to let someone (or some contract) spend any ID from an NFT collection. So, you only need to approve one time per NFT collection (even if there are multiple ids).

## Why can't I swap ETH?
Ethereum has a different permissions model than the ERCs (e.g. ERC20, ERC721, and ERC1155). Generally speaking, no one can take ETH out of your address except you (by spending it on gas or sending it). So, you have to wrap it into WETH first so it can play nicely with the ERC20 standards of the 0x contracts (which Sudoswap uses). 

## Which networks are supported?
Only Ethereum Mainnet is supported. Testnets and layer 2s are currently unsupported. 
