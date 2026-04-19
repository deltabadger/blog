---
title: "Coldcard vs. Trezor vs. Jade vs. BitBox"
description: "If you're looking for a hardware wallet for your Bitcoin or other assets, I give you four options and my recommendation."
published: false
---

If you're looking for a hardware wallet for your Bitcoin or other assets, I give you four options and my recommendation.

*Check also our reviews of [Ledger Flex](/academy/ledger-flex) and [Ledger Stax](/academy/ledger-stax)*

Let's not waste time, lads and gents, the "big four":

<figure>
    <img src="/blog/wallet-coldcard.webp" alt="ColdCard Mk4">
    <figcaption>
        <a href="https://store.coinkite.com/store" target="_blank" rel="nofollow">
            ColdCard Mk4 $157
        </a>
    </figcaption>
</figure>

**Coldcard Mk4** is built for maximum security and Bitcoin protocol compatibility. It offers a range of advanced security features and works on all operating systems with compatible wallets like Electrum or Nunchuk, though it lacks a dedicated app. The user experience is a bit "clunky," but this is a trade-off for advanced features, support for complex multisig setups, and large multi-UTXO transactions. Coldcard is not fully open-source, which is controversial for many, but this can also be seen as a security advantage. Up to you to decide.

<figure>
    <img src="/blog/wallet-trezor-safe-3-btc.avif" alt="Trezor Safe 3">
    <figcaption>
        <a href="https://trezor.io/trezor-safe-3-bitcoin-only" target="_blank" rel="nofollow">
            Trezor Safe 3 (Bitcoin-only) €79
        </a>
    </figcaption>
</figure>

**Trezor Safe 3** offers, in my opinion, the best user experience. Manufactured by SatoshiLabs, the company that created the first Bitcoin hardware wallet, Trezor has a longstanding reputation and fully open-source software, including an upcoming open-source security chip. Trezor stick is my go-to recommendation for people who ask without very specific needs. It has dedicated apps on all platforms, though on iOS, it's view-only due to Apple's limitations on USB usage. It's also a solid choice if you're interested in multi-asset support down the road, including MetaMask support. If you're considering Trezor's premium Safe 5 model instead, check out my [detailed comparison of Safe 3 vs. Safe 5](/academy/trezor-safe-3-vs-trezor-safe-5).

<figure>
    <img src="/blog/wallet-jade.webp" alt="Blockstream Jade">
    <figcaption>
        <a href="https://store.blockstream.com/products/blockstream-jade-hardware-wallet" target="_blank" rel="nofollow">
            Blockstream Jade €80.95
        </a>
    </figcaption>
</figure>

**Jade** is an affordable open-source Bitcoin-only wallet developed by Blockstream—a major contributor to Bitcoin's core infrastructure. Jade stands out with native support for the Liquid Network and Blockstream's Green Wallet app. Although it lacks a secure element, it uses an innovative alternative cryptographic solution ("virtual secure element") designed by true experts in the field. It's compatible with all platforms and can connect via Bluetooth, adding flexibility and convenience for mobile users.

<figure>
    <img src="/blog/wallet-bitbox.jpg" alt="BitBox02">
    <figcaption>
        <a href="https://shop.bitbox.swiss/en/products/bitbox02-bitcoin-only-4" target="_blank" rel="nofollow">
            BitBox02 (Bitcoin-only) €149.00
        </a>
    </figcaption>
</figure>

**BitBox02** is relatively new to the game and features a secure chip and microSD card backup for easy recovery. This fully open-source wallet has a native app for all systems except iOS. It supports a limited range of additional blockchains as well but, unlike Trezor, does not integrate with MetaMask. That's not an issue for those focused on Bitcoin. It's worth noting that BitBox02 hardware performs very well with complex multi-UTXO transactions.

Note that both Trezor and BitBox02 offer Bitcoin-only versions, which enhance UX and security by reducing the *attack surface*. However, once you choose the Bitcoin-only model, you can't convert it into a multicoin version later.

## TL;DR:

Each of the devices above is excellent—wallets I wouldn't recommend simply didn't make the list. When it comes to security, it's a nuanced topic, and hardware wallet vulnerabilities aren't typically top of the list. Keeping your wallet physically secure is always critical, but remember that your paper seed backup is more vulnerable. Most attacks involve social engineering, where you might accidentally expose your keys on a shady site pretending to be Coinbase. **Never put your private keys anywhere outside of the hardware wallet itself.**

Once you've secured your Bitcoin with a hardware wallet, consider setting up a [crypto DCA](/) bot to build your position with smart recurring purchases.

### Reasons to Buy:

- **Coldcard**: Best multisig and large transactions support, top hardware security, works on iOS
- **Trezor Safe 3**: best user experience, low price, open-source, strong reputation
- **Jade**: Liquid Network support, low price, open-source, Bluetooth, works on iOS
- **BitBox02**: User-friendly, open-source, Swiss-built

### Reasons for "Nay":

- **Coldcard**: No native app, not fully open-source, nerdy user experience
- **Trezor Safe 3**: View-only on iOS
- **Jade**: Lacks a physical secure element, budget build
- **BitBox02**: No iOS or MetaMask support

## Comparison Table

| Feature            | Coldcard | Trezor | Jade   | BitBox02 |
|--------------------|----------|--------|--------|----------|
| Price              | $157     | €79    | €80.95 | €149.00  |
| UX                 | 3/5      | 5/5    | 4/5    | 4/5      |
| Secure Element     | 5/5      | 5/5    | 3/5    | 5/5      |
| Open-source        | 3/5      | 5/5    | 5/5    | 5/5      |
| Native App         | 1/5      | 5/5    | 5/5    | 5/5      |
| iOS                | 5/5      | 2/5    | 5/5    | 1/5      |
| Large Transactions | 5/5      | 3/5    | 4/5    | 5/5      |
| Multisig Support   | 5/5      | 3/5    | 4/5    | 4/5      |
| Liquid Network     | 1/5      | 1/5    | 5/5    | 1/5      |
| Bluetooth          | 1/5      | 1/5    | 5/5    | 1/5      |
| Multicoin Option   | 1/5      | 5/5    | 1/5    | 4/5      |

## References

1. [Coldcard Advanced Bitcoin Protocol Features](https://coldcard.com/docs/compare-other-wallets)
2. [First Open-source Secure Element by SatoshiLabs (Trezor)](https://blog.trezor.io/introducing-tropic-square-why-transparency-matters-a895dab12dd3)
3. [Trezor — supported coins](https://trezor.io/coins)
4. [Virtual Secure Element: Blockstream Jade Security Model](https://help.blockstream.com/hc/en-us/articles/15884462476953-Blockstream-Jade-Security-Model-FAQs)
5. [BitBox — supported coins](https://bitbox.swiss/coins)
6. [Multisig Setup and Large Multi-UTXO Transactions — Wallet Test](https://blog.casa.io/bitcoin-multisig-hardware-signing-performance-2024)
