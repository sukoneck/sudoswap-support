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
- [Are my assets locked once I create a swap?](#are-my-assets-locked-once-I-create-a-swap)
- [What happens if my parter accepts a swap but I don't have the assets any more?](#what-happens-if-my-parter-accepts-a-swap-but-i-dont-have-the-assets-any-more)
- [Do I have to approve all of my assets?](#do-I-have-to-approve-all-of-my-assets)


<!-- 
  "how-to" is for when you want to know how to do something 
 -->

# How-to FAQ

## How do I add (W)ETH to a swap? 
1. We can only swap ERC20, ERC721, and ERC1155. So, we swap [WETH](https://etherscan.io/token/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2) which is ERC20, never pure ETH.
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
There are two common reasons that a swap fails:
1. One or both people have already sent one of the assets somewhere else. So, the swap is no longer able to be filled. 
2. An approval transaction hasn't successfully completed yet for one or more of the assets. So, the swap is not yet able to complete the swap. 

<!-- 
  "how it works" is for when you want to understand the service  
 -->

# How sudoswap.xyz works FAQ

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
Yes. If you're swapping multiple items you need to approve each of them. There is unfortunately no way around this. 
