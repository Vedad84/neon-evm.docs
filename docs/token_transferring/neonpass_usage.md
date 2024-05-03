---
title: Move Tokens Between Neon EVM and Solana
proofedDate: 20231207
iterationBy: na
includedInSite: true
approvedBy: HB
comment:
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
/* import image1 from '@site/static/img/doc-images/neonpass/connect-wallets.png';
import image2 from '@site/static/img/doc-images/neonpass/transfer.png';
import image3 from '@site/static/img/doc-images/neonpass/select_network.png';
import image4 from '@site/static/img/doc-images/neonpass/transfer1.png';
import image5 from '@site/static/img/doc-images/neonpass/transfer-solana-neon.png';
import image6 from '@site/static/img/doc-images/neonpass/transfer_complete_solana_neon.png';
import image7 from '@site/static/img/doc-images/neonpass/confirmation_transfer_neonscan.png';
import image8 from '@site/static/img/doc-images/neonpass/confirmation_transfer_solana.png'; */

import image1 from '@site/static/img/doc-images/neonpassV2/Connect_to_wallet.png';
import image2 from '@site/static/img/doc-images/neonpassV2/Neon_to_Solana.png';
import image3 from '@site/static/img/doc-images/neonpass/select_network.png';
import image4 from '@site/static/img/doc-images/neonpassV2/Solana_to_Neon_transfer.png';
import image5 from '@site/static/img/doc-images/neonpassV2/Transfer_completed_general.png';
import image6 from '@site/static/img/doc-images/neonpassV2/Transfer_completed_general.png';
import image7 from '@site/static/img/doc-images/neonpass/confirmation_transfer_neonscan.png';
import image8 from '@site/static/img/doc-images/neonpass/confirmation_transfer_solana.png';
import image9 from '@site/static/img/doc-images/neonpassV2/Not_Enough_SOL.png';
import image10 from '@site/static/img/doc-images/neonpassV2/Wrong_network.png';
import image11 from '@site/static/img/doc-images/neonpassV2/Transfer_completed.png';
import image12 from '@site/static/img/doc-images/neonpassV2/Transfer_failed.png';
import image13 from '@site/static/img/doc-images/neonpassV2/Homepage.png';
import image14 from '@site/static/img/doc-images/neonpassV2/Mobile Wallet connect.png';
import image15 from '@site/static/img/doc-images/neonpassV2/Transfer complete.png';
import image16 from '@site/static/img/doc-images/neonpassV2/Transfer_failed.png';

## TL;DR

- Transfer tokens to and from Solana and Neon networks with our [intuitive UI](https://neonpass.live/)
- No wrapping

## Overview

This guide demonstrates how to transfer tokens between Solana and Neon EVM using the [NeonPass](https://neonpass.live/) UI. The same tooling is available as an [npm package](/docs/developing/integrate/neon_transfer).

You can transfer tokens in either direction, but each transaction incurs a gas fee in either NEON or SOL or the token of your choice with which you are transacting.

:::info
 Neon EVM's Devnet now supports a feature providing the option to pay the gas fees with the [token of transaction](https://neonevm.org/blog/feature-alternative-gas-fee-token), rather than only NEON or SOL.
:::

> Under the hood, transferring tokens from Neon EVM to Solana requires the transaction fees to be paid in NEON or (if supported) the transaction token as per the user's choice; whereas transferring tokens from Solana to Neon EVM requires the transaction fees to be paid in either NEON or SOL.
>
> ## Important Note for First-Time Transfers

:::caution
When transferring tokens from Neon EVM to Solana for the first time, ensure that you have SOL in your Solana wallet to cover the transaction costs. This is a one-time requirement for the initial transfer.
:::

## Prerequisites

- EVM-compatible wallet (e.g. Atomic Wallet, MetaMask, etc.)
- Solana-compatible wallet (e.g. Phantom, Solfare, etc.)
- Browser with both wallet applications attached
- Token balance to pay gas fees

## Transfer tokens with NeonPass

### Step 1: Set up wallets

1.1 Navigate to [NeonPass](https://neonpass.live/).

1.2 Add your required Neon EVM network in your EVM-compatible wallet through [Chainlist.org/chain/245022934](https://chainlist.org/?chain=245022934&search=Neon+EVM&testnets=true).

> For further help, see our [wallet setup walkthrough](/docs/wallet/metamask_setup).

### Step 2: Connect wallets to NeonPass

:::tip

Remember to use a browser to which both your Solana- and EVM-compatible wallets are attached.

:::

2.1 Select the network you want to connect to from the dropdown in the top right corner.
<img src={image3} width="450" style={{ display: 'block', margin: '10px auto' }} />

2.2 Click **Connect Wallet** to connect your Solana-compatible wallet to NeonPass. Follow the login procedure in your wallet's popup window and ensure it's connected to the network you require (e.g. Mainnet).
<img src={image1} width="450" style={{ display: 'block', margin: '10px auto' }} />

:::tip

Ensure you have enough funds to pay the withdrawal approval fee.

:::

2.3 Repeat this step for your EVM-compatible wallet.

After successfully connecting your wallets to NeonPass, the **Connect Wallet** text changes to the name of the network (Solana or Neon), and the public key of your accounts is displayed.

### Step 3: Conduct transfer

<Tabs>
  <TabItem value="neontosolana" label="Neon EVM to Solana" default>

3.1 Use the arrow to determine the direction of transfer (from Neon EVM to Solana).

<img src={image2} width="450" style={{ display: 'block', margin: '10px auto' }} />

3.2 Use the dropdown to select the token you want to transfer and enter the amount you want to send.

</TabItem>

<TabItem value="solanatoneon" label="Solana to Neon EVM">

3.1 Use the arrow to determine the direction of transfer (from Solana to Neon EVM).

<img src={image4} width="450" style={{ display: 'block', margin: '10px auto' }} />

3.2 Select token to transfer and token to pay in:

a. Select the token using the drop-down and enter the amount you want to send.

- For sending NEON tokens from Solana to Neon EVM:
  1. Select NEON from the token dropdown.
  2. Enter the amount of NEON you want to transfer.
  3. Choose between NEON and SOL as the gas token using the selector options below the `Transfer` button.

- For sending SPL tokens (e.g., USDC) from Solana to Neon EVM:
  1. Select the desired SPL token from the token dropdown.
  2. Enter the amount of the SPL token you want to transfer.
  3. Note that only SOL can be used as the gas token for SPL token transfers.

b. Use the selector options below the `Transfer` button to pay in NEON or SOL.

:::info Gas Token Selection
When transferring NEON tokens from Solana to Neon EVM, you can choose between NEON and SOL as the gas token. However, for other SPL tokens like USDC, only SOL can be used as the gas token.
:::

<!-- <img src={image5} width="450" style={{ display: 'block', margin: '10px auto' }} /> -->

</TabItem>
</Tabs>

3.3. Click **Transfer**.

3.4 Confirm the transaction in your sending wallet.

> Always verify the transaction details and only approve if you wish to proceed.

A successful transaction is confirmed.

<img src={image6} width="450" style={{ display: 'block', margin: '10px auto' }} />

3.5 Don't trust: verify

<Tabs>
  <TabItem value="neonscan" label="NeonScan" default>

To verify the transaction, click **View on Neon Explorer** to confirm on [NeonScan](https://neonscan.org) that the tokens were transferred. In the following example, 42 NEON were transferred out of Neon EVM.

<img src={image7} width="450" style={{ display: 'block', margin: '10px auto' }} />

Let's also check the destination Solana wallet address on [Solana Explorer](https://explorer.solana.com/) to verify the arrival of those 42 NEON tokens.

<img src={image8} width="450" style={{ display: 'block', margin: '10px auto' }} />

  </TabItem>

  <TabItem value="blockscout" label="Blockscout" default>

  Alternatively, use Blockscout's dedicated explorer [neon.blockscout.com](https://neon.blockscout.com) to search by transaction hash.

  </TabItem>
</Tabs>

We hope that you love NeonPass and that you are ready to leverage the full potential of Neon EVM by facilitating hassle-free transfers of assets to and from Solana.

## Transferring Tokens with NeonPass: Detailed Use Cases

<Tabs>
  <TabItem value="case1" label="SPL to Neon EVM" default>

### Case 1: Transferring SPL Tokens from Solana to Neon EVM 🌉

Follow these steps to transfer SPL tokens from your Solana wallet to Neon EVM:

1. Connect your Solana and Neon EVM wallets:
   - Choose a Solana-compatible wallet and connect it to NeonPass. Your Solana wallet address will be displayed once connected.
   - Choose a Neon-compatible wallet and connect it to NeonPass. Your Neon EVM wallet address will be displayed once connected.
   - If the wallet connection fails, an error message will be shown. If successful, a confirmation message will appear.

:::tip
Make sure you have enough SOL in your Solana wallet to cover the gas fees for the transfer. 💸
:::

2. Select the token you wish to transfer from the dropdown list:
   - The dropdown list displays the ticker and balance of each token in your connected wallet.
   - Tokens with a balance will be displayed at the top of the list in alphabetical order.

3. Enter the token amount you want to transfer:
   - Click the "MAX" button to automatically enter your entire wallet balance for the selected token.
   - The "You will receive" field will display the total value you will receive in Neon EVM.
   - If your account balance is insufficient to cover the gas fees, an "Insufficient funds for gas" message will appear.
   - The "Transfer" button will be active if your balance is sufficient and the entered amount is greater than 0.

4. Select the token to pay for gas fees (if transferring NEON):
   - If you're transferring NEON tokens, you can choose between NEON and SOL to pay for the gas fees.
   - For other SPL tokens like USDC, only SOL can be used as the gas token.

:::info
When transferring NEON tokens from Solana to Neon EVM, you have the option to pay gas fees in either NEON or SOL. For other SPL tokens, gas fees can only be paid in SOL. ⛽️
:::

5. (Optional) Select the priority fee for your transaction in the Advanced mode:
   - Choose between Standard, Medium, or Fast priority fees.
   - The priority fee value will be displayed in the selected token and USD.

6. Click on "Transfer":
   - A "Transaction has been sent" message will be displayed.
   - The "Transfer in progress" screen will appear, showing the estimated time for the transfer to complete.

7. Sign the transaction:
   - Approve the transfer by signing the transaction in your connected wallets.

8. Review the transaction summary:
   - If the transaction is successful, the "Transfer Completed" screen will be shown, displaying the amount received and the updated token balances in your Neon EVM wallet.
   - If the transfer fails, a "Transfer has failed" screen will appear.

:::success
Congratulations! 🎉 You have successfully transferred your SPL tokens from Solana to Neon EVM.
:::

  </TabItem>

  <TabItem value="case2" label="Neon EVM to SPL">

### Case 2: Withdrawing NEON / ERC-20 Tokens from Neon EVM to SPL Solana 💸

Follow these steps to withdraw NEON or ERC-20 tokens from Neon EVM to your Solana wallet:

1. Connect your Neon EVM and Solana wallets:
   - Choose a Neon-compatible wallet and connect it to NeonPass. Your Neon EVM wallet address will be displayed once connected.
   - Choose a Solana-compatible wallet and connect it to NeonPass. Your Solana wallet address will be displayed once connected.
   - If the wallet connection fails, an error message will be shown. If successful, a confirmation message will appear.

2. Select the token you wish to transfer from the dropdown list:
   - The dropdown list displays the ticker and balance of each token in your connected Neon EVM wallet.
   - Tokens with a balance will be displayed at the top of the list in alphabetical order.

3. Enter the token amount you want to transfer:
   - Click the "MAX" button to automatically enter your entire wallet balance for the selected token.
   - The "You will receive" field will display the total value you will receive in your Solana wallet.
   - If your account balance is insufficient to cover the gas fees, an "Insufficient funds for gas" message will appear.
   - The "Transfer" button will be active if your balance is sufficient and the entered amount is greater than 0.

4. Click on "Transfer":
   - A "Transaction has been sent" message will be displayed.
   - The "Transfer in progress" screen will appear, showing the estimated time for the transfer to complete.

5. Sign the transaction:
   - If you have an existing Solana account with sufficient SOL balance, approve the transfer by signing the transaction in your Neon-compatible wallet.
   - If you're withdrawing to a new Solana account, you'll need to sign the transaction in both your Neon-compatible wallet (to approve the ERC-20 transfer) and your Solana-compatible wallet (to transfer tokens from Neon EVM to Solana). Ensure that you have enough SOL in your Solana wallet to cover the gas fees.
   - If you're withdrawing an ERC-20 token to an existing Solana wallet that has never received that specific token before, you'll need to have enough SOL in your Solana wallet to cover the gas fees.
   - If you're transferring wNEON, NeonPass will unwrap it to NEON before transferring.

:::caution
When withdrawing to a new Solana account or an existing account that has never received the specific ERC-20 token before, ensure that you have sufficient SOL in your Solana wallet to cover the gas fees. ⚠️
:::

6. Review the transaction summary:
   - If the transaction is successful, the "Transfer Completed" screen will be shown, displaying the amount received and the updated token balances in your Solana wallet.
   - If the transfer fails, a "Transfer has failed" screen will appear.

:::success
Well done! 👏 You have successfully withdrawn your NEON or ERC-20 tokens from Neon EVM to your Solana wallet.
:::

  </TabItem>

  <TabItem value="case3" label="CEX to Neon EVM">

### Case 3: Buying NEON on a CEX, Withdrawing to Solana, and Transferring to Neon EVM 🔄

Follow these steps to buy NEON on a centralized exchange (CEX), withdraw it to your Solana wallet, and then transfer it to Neon EVM:

1. Buy NEON on a CEX that supports SPL tokens.

2. Withdraw the purchased NEON tokens to your Solana wallet.

:::tip
Double-check the withdrawal address to ensure you are sending the NEON tokens to the correct Solana wallet. 🔍
:::

3. Connect your Solana and Neon EVM wallets to NeonPass:
   - Choose your Solana-compatible wallet and connect it to NeonPass. Your Solana wallet address will be displayed once connected.
   - Choose your Neon-compatible wallet and connect it to NeonPass. Your Neon EVM wallet address will be displayed once connected.
   - If the wallet connection fails, an error message will be shown. If successful, a confirmation message will appear.

4. Select NEON from the dropdown list in the "Send" field.

5. Enter the amount of NEON you want to transfer to your Neon EVM wallet.

6. Choose NEON as the gas token to pay for the transaction fees.

:::info
In this case, you can use NEON as the gas token since you are transferring NEON tokens from Solana to Neon EVM. 🪙
:::

7. Click on "Transfer":
   - A "Transaction has been sent" message will be displayed.
   - The "Transfer in progress" screen will appear, showing the estimated time for the transfer to complete.

8. Sign the transaction in your connected wallets to approve the transfer.

9. Review the transaction summary:
   - If the transaction is successful, the "Transfer Completed" screen will be shown, displaying the amount of NEON received in your Neon EVM wallet and the updated balance.
   - If the transfer fails, a "Transfer has failed" screen will appear.

:::success
Fantastic! 🚀 You have successfully bought NEON on a CEX, withdrawn it to your Solana wallet, and transferred it to your Neon EVM wallet.
:::

  </TabItem>
</Tabs>

## Edge Cases and Considerations 🔍

When transferring tokens using NeonPass, there are a few edge cases and considerations to keep in mind. This section will cover some of these scenarios to help you navigate the process smoothly.

<!-- <img src={image3} width="450" style={{ display: 'block', margin: '10px auto' }} /> -->
<!-- <img src={edgeCasesImage} alt="Edge cases" /> -->

1. Insufficient funds for gas fees 💸
   If your wallet balance is insufficient to cover the gas fees for the token transfer, you will see a warning message indicating "Insufficient funds for gas". In this case, you will need to ensure that you have enough balance in the appropriate token (NEON or SOL) to cover the gas fees before proceeding with the transfer.

  <img src={image9} width="450" style={{ display: 'block', margin: '10px auto' }} />
   <!-- <img src={insufficientFundsImage} alt="Insufficient funds for gas" /> -->

2. Wallet connection issues 🚫
   If there are any issues connecting your wallet to NeonPass, you will see a warning message indicating the specific problem. Some common wallet connection issues include:
   
   - Wallet disconnected: This message appears when your wallet is not connected or has been disconnected during the process.
   - Wallet connection failed: This message indicates that there was an error while attempting to connect your wallet to NeonPass.
   
   <img src={image10} width="450" style={{ display: 'block', margin: '10px auto' }} />
   <!-- <img src={walletConnectionIssuesImage} alt="Wallet connection issues" /> -->

   If you encounter any of these issues, please check your wallet connection and try again.

3. Transfer completion and failure ✅❌
   After initiating a token transfer, you will see a confirmation message indicating whether the transfer was successful or if it failed.
   
   - Transfer completed: If the token transfer is successful, you will see a "Transfer completed" message, along with a summary of the transaction details.
   <img src={image11} width="450" style={{ display: 'block', margin: '10px auto' }} /> 
   - Transfer failed: If the token transfer fails for any reason, you will see a "Transfer failed" message. In this case, please check your wallet balance, gas fees, and network status, and try again.

    <img src={image12} width="450" style={{ display: 'block', margin: '10px auto' }} />
   <!-- <img src={transferCompletionImage} alt="Transfer completion" />
   <img src={transferFailureImage} alt="Transfer failure" /> -->

:::info
If you encounter any persistent issues or have questions about edge cases not covered here, please reach out to our support team for assistance. 🙋‍♂️
:::

By understanding these edge cases and considerations, you can better prepare for and navigate any potential challenges during the token transfer process using NeonPass.

## Using NeonPass on Mobile Devices 📱

NeonPass is designed to be responsive and user-friendly across various devices, including mobile phones. This section will guide you through the mobile experience of transferring tokens using NeonPass.

<img src={image13} width="450" style={{ display: 'block', margin: '10px auto' }} /> 
<!-- <img src={mobileOverviewImage} alt="NeonPass mobile overview" /> -->

1. Connecting wallets on mobile 🔗
   To connect your wallets on a mobile device, follow these steps:
   
   - Open the NeonPass web app in your mobile browser.
   - Tap on the "Connect Wallet" button for the wallet you want to connect (e.g., Solana or Neon EVM).
   - Follow the prompts in your mobile wallet app to approve the connection.
   - Once connected, your wallet address will be displayed in the NeonPass interface.

  <img src={image14} width="450" style={{ display: 'block', margin: '10px auto' }} /> 
   <!-- <img src={mobileWalletConnectionImage} alt="Mobile wallet connection" /> -->

   :::tip
   Make sure you have your mobile wallet apps installed and set up before attempting to connect them to NeonPass. 💡
   :::

2. Selecting tokens and entering amounts 🪙
   The process for selecting tokens and entering transfer amounts on mobile is similar to the desktop experience:

   - Tap on the token dropdown menu to select the token you want to transfer.
   - Enter the amount you want to transfer in the designated input field.
   - If you want to transfer the maximum available balance, tap on the "MAX" button.

   <!-- <img src={mobileTokenSelectionImage} alt="Mobile token selection" /> -->

3. Initiating and confirming transfers ✅
   To initiate a token transfer on mobile, follow these steps:

   - After selecting the token and entering the amount, tap on the "Transfer" button.
   - Review the transaction details in the confirmation popup.
   - If everything looks correct, tap on "Confirm" to proceed with the transfer.
   - Your mobile wallet app will prompt you to approve the transaction. Follow the instructions in your wallet app to complete the approval process.
  
  <img src={image15} width="450" style={{ display: 'block', margin: '10px auto' }} /> 
   <!-- <img src={mobileTransferConfirmationImage} alt="Mobile transfer confirmation" /> -->

   :::caution
   Always double-check the transaction details before confirming a transfer, especially on mobile devices where screen sizes are smaller. 🔍
   :::

4. Tracking transfer progress and history 📊
   You can track the progress and history of your token transfers on mobile as well:

   - After initiating a transfer, you will see a progress screen indicating the status of your transaction.
   - Once the transfer is complete, you can view the transaction details and updated balances in the NeonPass interface.
   - To view your transfer history, tap on the "History" tab in the NeonPass mobile UI.

   <!-- <img src={mobileTransferProgressImage} alt="Mobile transfer progress" />
   <img src={mobileTransferHistoryImage} alt="Mobile transfer history" /> -->

By following these steps, you can easily transfer tokens using NeonPass on your mobile device, enjoying a seamless and user-friendly experience on the go.

## Under the hood

Neon EVM isn't a blockchain, and so it follows that NeonPass isn't a conventional blockchain bridge. Your assets are not wrapped. Instead, Neon EVM applies an ERC-20 interface, making SPL tokens behave like Ethereum-natives when in the Neon network. [Learn more about how NeonPass works](/docs/tokens/token-accounts).
