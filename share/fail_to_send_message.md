## Problem: 

After a system of network instability, the network returns to normal and starts sealing sectors, precommit provecommit messages cannot be sent out

## Environment:

lotus version 1.13.0

## Resolution:

1: Go to your browser and look for the nonce of the last message of your address  
2: Locally check the nonce of all the messages that are stuck, find the smallest value and use the command lotus mpool pending --local to sort the output by filtering it yourself  
3: To fill in the missing nonce, you can use the command lotus send --nonce <missing-nonce> --from <your-wallet> <your-wallet-too> amount, note that the nonce is increasing, so you have to fill it in from small to large  
4: After this. your local message will be sent normally.

## Extras:

The solution process is as follows.  
Tried to add GAS charges, no luck, messages are still backlogged locally.
Tried to send a transfer message, prompt: message nonce doesn't match next nonce.
At this point, it is thought that some messages are taking up nonce but not being sent because of network instability.