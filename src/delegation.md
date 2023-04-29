# Delegation

Any hotkey may become a delegate and receive nominations of stake from other
wallets in the network. Key owners of delegates collect an 18% "take" on
emissions of all delegated Tao.

When a coldkey creates a hotkey delegate, it will receive all of the emissions
from the stake it adds to its hotkey delegate. The delegate owner will also
collect 18% of the emissions from all delegated stake.

## Turn your hotkey into a delegate:

```bash
btcli nominate
```

## Stake to a delegate account:

```bash
btcli delegate
```

## List all the delegates in the network:

```bash
btcli list_delegates
```

## Show who you are delegating to:

```bash
btcli my_delegates
```


**E** = emissions earned by the key per block

**Sn** = Stake from owner

**St** = Total stake on hotkey

**Delegate key owner**

\\[
  Emissions\\ received =
  \mathrm{E} \cdot 0.18 +
    \left(
      \mathrm{Sn} / \mathrm{St}
    \right)
    \cdot
    \left(
      \mathrm{E} - \mathrm{E}
      \cdot
      0.18
    \right)
\\]

*~delegates receive an 18% tax*

**Delegated stake owners**

\\[
  Emissions\\ received =
    \left(
      \mathrm{Sn} / \mathrm{St}
    \right)
    \cdot
    \left(
      \mathrm{E} - \mathrm{E}
      \cdot
      0.18
    \right)
\\]

*~delegated stake owners pay an 18% tax through emissions*

