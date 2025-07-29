# bip_utils

Biblioteca Python para manipulação de carteiras, chaves e endereços de múltiplas criptomoedas.

## Visão Geral

O bip_utils é uma biblioteca modular que oferece ferramentas para geração, validação e manipulação de carteiras, endereços e chaves privadas/públicas de diversas blockchains, suportando padrões amplamente utilizados como BIP32, BIP39, BIP44, BIP49, BIP84, BIP86, SLIP32, além de formatos específicos de moedas como Bitcoin, Ethereum, Cardano, Solana, Monero, Algorand, entre outras.

## Principais Funcionalidades
- Geração e validação de endereços para várias criptomoedas
- Suporte a carteiras HD (Hierarchical Deterministic)
- Implementação de padrões de mnemônicos (BIP39, Electrum, Monero, Algorand, etc)
- Utilitários para codificação/decodificação em Base58, Bech32, SS58, WIF, entre outros
- Ferramentas para curvas elípticas (ECC) e funções criptográficas (SHA, HMAC, Blake2b, etc)
- Suporte a brainwallets e tokens SPL (Solana)

## Estrutura do Projeto
- `addr/` - Manipulação de endereços de diversas moedas
- `algorand/` - Suporte a Algorand e seus mnemônicos
- `base58/`, `bech32/`, `ss58/` - Codificações específicas
- `bip/` - Implementação dos padrões BIP (BIP32, BIP39, BIP44, etc)
- `brainwallet/` - Brainwallets
- `cardano/` - Suporte a Cardano (Byron, Shelley, CIP1852)
- `coin_conf/` - Configurações de moedas
- `ecc/` - Algoritmos de curvas elípticas
- `electrum/` - Suporte a carteiras e mnemônicos Electrum
- `monero/` - Suporte a Monero
- `slip/` - Implementação de SLIP32, SLIP44, etc
- `solana/` - Suporte a Solana
- `substrate/` - Suporte a Substrate/Polkadot
- `utils/` - Utilitários criptográficos e de manipulação
- `wif/` - Codificação WIF

## Exemplo de Uso
```python
from bip_utils import Bip39MnemonicGenerator, Bip44, Bip44Coins

# Gerar uma frase mnemônica BIP39
mnemonic = Bip39MnemonicGenerator().FromWordsNumber(12)
print(f"Mnemonic: {mnemonic}")

# Criar uma carteira BIP44 para Bitcoin
bip44_wallet = Bip44.FromMnemonic(mnemonic, Bip44Coins.BITCOIN)
account = bip44_wallet.Purpose().Coin().Account(0)
address = account.Change(Bip44Changes.CHAIN_EXT).AddressIndex(0).PublicKey().ToAddress()
print(f"Primeiro endereço Bitcoin: {address}")
```

## Público-Alvo
Desenvolvedores Python que precisam integrar funcionalidades de carteiras, chaves e endereços de múltiplas criptomoedas em seus sistemas, como exchanges, wallets, validadores, ferramentas de auditoria, etc.

## Licença
Consulte o arquivo de licença do projeto para mais detalhes.
