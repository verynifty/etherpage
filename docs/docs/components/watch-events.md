---
sidebar_label: 'WatchEvents'
sidebar_position: 5
---

# Events

Retrieve events in live from a smart contract and display them.


Properties:
* `address`
* `abi`
* `eventName`
* `args` optional

For convenience the properties are same as the [viem/wagmi libraries](https://viem.sh/docs/actions/public/getLogs.html).

## Example

This examples display USDC transfers as Toas notifications.

```
<WatchEvents
  address="0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48"
  abi={ABIs.ERC20}
  eventName="Transfer"
  onReceivedLogs={async function (logs) {
    console.log("Received logs", logs);
    for (const log of logs) {
      await sleep(400);
      Toast.success(
        formatAddress(log.args.from) +
          " sent " +
          parseInt(log.args.value) / 10e8 +
          " to " +
          formatAddress(log.args.to),
        {
          position: "bottom-left",
        }
      );
    }
  }}
/>

```

## Full example

* [USDC transfers live](https://fastdapp.xyz/editor?template=watch_events)


