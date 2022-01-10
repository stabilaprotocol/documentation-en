# Releases

### Signature Verification

You can verify the signature by stabilaweb.

```js
const Stb = require('stabilaweb').Stb;

console.log(Stb.verifySignature(SHA256, ADDRESS, SIGNATURE));
```

Suppose we got a `FullNode.jar` with a SHA256 hash `2fca93b09da4ac62641e03838e77fce99b4711ddb0c09aa91656c80fc9556d2e`, and a Stabila signature `21435e32131feb6d00ba8048df04e112e02569ec851064d8ecad2d4dd5da44b7628ddce16823dadfff6fd683fc58cee74964970621a845ee459e2c96a750de551b`.

To verify the integrity of the released file:

```shell
# First calculate the sha256 hash

sha256sum FullNode.jar  # or shasum -a 256 FullNode.jar (macOS)
# 2fca93b09da4ac62641e03838e77fce99b4711ddb0c09aa91656c80fc9556d2e  FullNode.jar

# Then check the signature

npm install -g stabilaweb
node -e 'console.log(require("stabilaweb").Stb.verifySignature(
    "2fca93b09da4ac62641e03838e77fce99b4711ddb0c09aa91656c80fc9556d2e",
    "SKeAcHxgErbVXrG3N3TZiSV6AT566BHTj2",
    "21435e32131feb6d00ba8048df04e112e02569ec851064d8ecad2d4dd5da44b7628ddce16823dadfff6fd683fc58cee74964970621a845ee459e2c96a750de551b"
  ))'
# true

# Now you've verified the integrity of the binary release file.
```

### Version Signature

- Odyssey-3.7

```shell
FullNode sha256sum: 2fca93b09da4ac62641e03838e77fce99b4711ddb0c09aa91656c80fc9556d2e
FullNode signature: 21435e32131feb6d00ba8048df04e112e02569ec851064d8ecad2d4dd5da44b7628ddce16823dadfff6fd683fc58cee74964970621a845ee459e2c96a750de551b
```

- GreatVoyage-4.0.0

```shell
FullNode sha256sum: d3f8f9fde64bdefaadae784d09de97172e5e8a3fe539217e12b89963983a530d
FullNode signature: e788dbaf2fe35f099f65b2403cfb0d7cbe7f4611f8c5ff8151e4bd84ae468d2e541043c9cde9e74500003027ae9f25cdda81a9bcd60abb45ca7a69f965f4dcc71c
```

- GreatVoyage-4.1.1

```shell
FullNode sha256sum: 30e716b86b879af1e006c2b463903ae3835e239e32e2b01c2a1b903a153897fe
FullNode signature: 5faee65a448bb9aa77835992ca3d24e50d8a76b7934f80664ad38e83179c8114278fdef4494de7231f8e40de86461676a7aa4a54c795f4c692e91d90e156ec471b
```

- GreatVoyage-v4.1.2

```shell
FullNode sha256sum: 4ded44b6c1a3dbd25212e14ab413142b5463dcbf30a528f83ded529048542547
FullNode signature: 57a094c1b8a5ec301ef913eb718de2498b5695eb999530863df05252ba8919ba6866c8490e29d36f7dbf34537c898ece5ef0111efb134419c3a5fd6fc9ec03b81c
```

- GreatVoyage-v4.1.3(Thales)

```shell
FullNode sha256sum: c5fb99ad5b024bb7877118f30fb6065f6e6febd11a3cfa241521cbed73cca181
FullNode signature: d80ec371e791c4316925d80ff3400cf51b14c8a4d4c696b7817c517eb094823622932b45b9b37f9e9657513c3eddb1134fbbb1ee56727c0957e8a3b40c67409b1c
```

- GreatVoyage-v4.2.0(Plato)

```shell
FullNode sha256sum:
bbf103432be016b582452137b4862140af15ccf7c5daa9be738450705317fdb8
FullNode signature:
326701699a5eb8d497eb454b5b74c1559961417fb6f262b4e6314052d73f5977312e0450937fa485236f51f706b434acf8659ce1325d704097c5748629e736ef1c
```

- GreatVoyage-v4.2.1(Origen)

```shell
FullNode sha256sum:
9888710c915a4027f1bc3dcb1d5d983e0c00d4c438f6fa307d412f62ff6862ea
FullNode signature:
6e7d8ef9d033ebf9213118b7511f4ecc5def97442844fbd34de3ef76dd417a0d45da3e2e70fc213475d7fc0a44df1c54732874d858ec980159c5dbffc975680a1c
```

- GreatVoyage-v4.2.2(Lucretius)

```shell
FullNode sha256sum:
8a7f8143b3351ea6b5d8e3dfc857b09256d363d4907ba3ab0288f67f77c2a58f
FullNode signature:
71c6300ace5cbf16d78a32aa4602c3f129cb768e32acffaecd17b4134b5955bf37efda1d27025e894e521184a21174e5eddf4e7d1f86761657827795cbddfcfd1c
```

- GreatVoyage-v4.2.2.1(Epictetus)

```shell
FullNode sha256sum:
8bd040a8db16ccba3e957ed3558b82d145928153a53f9688302849658a72f9bc
FullNode signature:
3137a8ba8fa5556e4c4a7597aec8f5f46ebb79a64edcf9e2925d2e3314afde3e0f42fd4080e5e4f4d3d1eff263d30478b0322e6dbcc71c43b534f614004b5c561b
```

- GreatVoyage-v4.3.0(Bacon)

```shell
FullNode sha256sum:
b5e993800cea5ca040758dd6b3c7438def03cbf1358468beb76ea45399a59298
FullNode signature:
8da6ac58129d78d948810e4bc7372dd8aef5232bfbc4c33ad8fb21e88314e3d97dd77509e0f03a98da32679495152ccd4a9d07541589822e5cf5d3d4f61877191b
```

- GreatVoyage-v4.4.0(Rousseau)

```shell
FullNode sha256sum:
bf7f962846f75139dd89ac6da32074cad33b2e172c0749abbed8773cc1ab1a37
FullNode signature:
56ed97f3451e3d731f799bad952750d56aa78a9a91a2688b4d6b956328ede7e01bae78037ad6ef1f9c682b566e954dfb958271f006e5cf0dcace5768d76fda6e1b
```

- GreatVoyage-v4.4.1(Protagoras)

```shell
FullNode sha256sum:
4a32918849dc8a7fedcb637ff4939389363726cb16c6a581e39253260668ee04
FullNode signature:
fd747f61705ef045143bd2d55b278ca347904323711e2e86b11cf1dd203f198443ab1a399767a570005bd5b2ea283187ccc41557ffb79c959b018e8d798b96f81c
```

- GreatVoyage-v4.4.2(Augustinus)

```shell
FullNode sha256sum:
70eba12350fa21e1b261927093090e7bdf0765592d19433c594149bd3707ef0a
FullNode signature:
14430f463e6fab3dd247aca6267b6aaf2f1869b455d95aee297208bd1561c6c67559d9c535e63e74bbef604141cc4ceec78367a75e6ca4d4ceb6513019329c9b1b
```

- GreatVoyage-v4.4.3(Pythagoras)

```shell
FullNode sha256sum:
c07637a1a4a9a289218554f4714caef90032e267b068411c7dd818d4af45e39f
FullNode signature:
2bf8d65adf556fe2c04b739c1f4e6e73058914cf642a7806ff85e57be2ff122e35cbf3d67b0bc8bad4fb827198ffd8e06f60111a167ecb0b3db0d8e571b8c67b1c
```
