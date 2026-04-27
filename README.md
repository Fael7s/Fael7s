# Olá! 👋

Este é o meu perfil do GitHub.

### ₿ Bitcoin Address Generator (Node.js)

Abaixo está um exemplo de como gerar um endereço Bitcoin e sua respectiva chave privada (WIF) utilizando JavaScript:

```javascript
const bitcoin = require('bitcoinjs-lib');
const bip39 = require('bip39');

// Gerar mnemônica (opcional)
const mnemonic = bip39.generateMnemonic();
const seed = bip39.mnemonicToSeedSync(mnemonic);

// Derivar chave privada
const root = bitcoin.bip32.fromSeed(seed);
const child = root.derivePath("m/44'/0'/0'/0/0");
const { address } = bitcoin.payments.p2pkh({
  pubkey: child.publicKey,
  network: bitcoin.networks.bitcoin
});

console.log("Endereço:", address);
console.log("Chave Privada (WIF):", child.toWIF());
```

---
> *Nota: Este código é para fins educacionais. Nunca compartilhe sua chave privada ou mnemônica com ninguém.*
