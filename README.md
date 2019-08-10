
# Blob Protocol
## Immutable & Deletable
### A protocol to reference data without storing it on-chain

Thanks to [Unwriter](https://github.com/unwriter) for the original B protocol.
Thanks to [Satchmo](https://github.com/rohenaz) for support.

```
OP_FALSE OP_RETURN
 1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4
 [Hash of the data]
 [Hash algorithm]
 [URL of the data]
 [Media type]
 [Encoding (optional if no filename)]
 [Filename (optional)]
```


**Example 1 (Bitcoin Whitepaper PDF)**

```
OP_FALSE OP_RETURN
 1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4
 b1674191a88ec5cdd733e4240a81803105dc412d6c6708d53ab94fc248f4f553
 SHA256
 https://bitcoin.org/bitcoin.pdf
 application/pdf
 binary
 bitcoin.pdf
```

**Example 2 (Bitcoin Whitepaper PDF with double SHA-256)**

```
OP_FALSE OP_RETURN
 1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4
 316a938a719b5200d53d3099870bcc8f02365a2d5b27a8ce29468f4a79ba75ac
 SHA256d
 https://bitcoin.org/bitcoin.pdf
 application/pdf
 binary
 bitcoin.pdf
```

**Example 3 (JPG hosted on imgur)**

```
OP_FALSE OP_RETURN
 1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4
 3118eedceddf2608bb1d51fa6423a107d73142abb57b6e93d2553458c1d20f95
 SHA256
 https://i.imgur.com/mVthyRf.jpg
 image/jpeg
```

## Intro

The Blob protocol uses OP_RETURN to reference data without storing it on-chain

## Protocol

The Bitcom prefix for the Blob protocol is `1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4`

The general structure of the protocol is:

```markdown
OP_RETURN
 1BLoBdFtWw7gnVbYM4CPGcq4eC8V3pfvM4
 [Hash]
 [Hash Algorithm]
 [URL]
 [Media type]
 [Encoding]
 [Filename]
```

1. **Hash:** Hash of the data stored at URL
2. **Hash Algorithm:** The hash algorithm used (SHA256, SHA256d, MD5, etc ..)
3. **URL:** URL pointing to the data
4. **Media Type:** As listed at https://www.iana.org/assignments/media-types/media-types.xhtml
5. **Encoding:** As listed at https://www.iana.org/assignments/character-sets/character-sets.xhtml (The default is `binary`)
6. **Filename:** A filename
