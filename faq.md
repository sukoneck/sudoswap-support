<!-- 
  when updating: 
    1. Add the answer to the relevant FAQ section
    2. Add the heading to the Contents section with a link to the header
 -->

# Contents

## [How-to FAQ](#how-to-faq)
- [How do I add (W)ETH to a swap?](#how-do-i-add-weth-to-a-swap) 

## [Troubleshooting FAQ](#troubleshooting-faq)
- *forthcoming*

## [How sudoswap.xyz works FAQ](#how-sudoswapxyz-works-faq)
- [Are my assets locked once I create a swap?](#are-my-assets-locked-once-I-create-a-swap)
- [What happens if my parter accepts a swap but I don't have the assets any more?](#what-happens-if-my-parter-accepts-a-swap-but-i-dont-have-the-assets-any-more)


<!-- 
  "how-to" is for when you want to know how to do something 
 -->

# How-to FAQ

## How do I add (W)ETH to a swap? 
1. We can only swap ERC20, ERC721, and ERC1155. So, we swap [WETH](https://etherscan.io/token/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2) which is ERC20, never pure ETH.
2. When creating a swap, select the `+ add assets` button
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

## *forthcoming*
- *forthcoming*

<!-- 
  "how it works" is for when you want to understand the service  
 -->

# How sudoswap.xyz works FAQ

## Are my assets locked once I create a swap?
No.

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
