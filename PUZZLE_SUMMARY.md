# GSMG.IO 5 BTC Puzzle Hunt - Setup Complete

## Overview
Successfully cloned and set up the GSMG.IO 5 BTC puzzle hunt repository. This is a comprehensive Bitcoin puzzle challenge with multiple phases involving cryptography, ciphers, and riddles.

## Repository Location
`/workspace/gsmgio-5btc-puzzle/`

## Puzzle Information

### Prize Details
- **Prize Address**: `1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe`
- **Original Prize**: 5 BTC
- **Current Prize**: 2.5 BTC (halved after Bitcoin halving on May 11, 2020)
- **Puzzle URL**: https://gsmg.io/puzzle

### Available Resources

#### Images
1. `puzzle.png` - The initial 14x14 binary matrix puzzle
2. `theseedisplanted.png` - Phase 2 puzzle image
3. `phase2.png` - Matrix Reloaded reference puzzle
4. `phase3.png` - Advanced phase with multiple parts
5. `SalPhaselonCosmicDuality.png` - Hidden phase puzzle
6. `photo_2020-04-26_09-24-30.jpg` - Decentraland hint

#### Documentation
- `README.md` - Complete walkthrough with hints and solutions

## Puzzle Phases Summary

### Phase 1: Binary Matrix
- 14x14 grid of colored squares (black/blue=1, yellow/white=0)
- Read counterclockwise in spiral from upper left
- Decodes to: `gsmg.io/theseedisplanted`

### Phase 2: The Seed Is Planted
- Hidden POST form on webpage
- Password: `theflowerblossomsthroughwhatseemstobeaconcretesurface`
- References Logic's song "The Warning"

### Phase 3: Matrix Reloaded
- Password: `causality`
- Involves AES-256-CBC encryption
- Requires SHA256 hashing
- Multiple sub-parts with complex riddles

### Phase 3.2: Advanced Decryption
- Password: `jacquefrescogiveitjustonesecondheisenbergsuncertaintyprinciple`
- Contains additional encrypted content

### Salphaseion (Hidden Phase)
- Accessed via SHA256 hash of puzzle text
- Multiple encoding schemes (binary, VIC cipher, Beaufort cipher)
- Currently partially solved

## Tools Required

### Cryptography Tools
- **OpenSSL** - For AES decryption
  ```bash
  openssl enc -aes-256-cbc -d -a -in <file> -pass pass:<sha256_hash>
  ```
- **SHA256 Calculator** - https://xorbin.com/tools/sha256-hash-calculator

### Cipher Tools
- **Beaufort Cipher**: https://ciphertools.co.uk/decode.php
- **VIC Cipher**: https://www.dcode.fr/vic-cipher
- **CyberChef**: https://gchq.github.io/CyberChef/

## Key Findings

### Important Passwords
1. `causality`
2. `theflowerblossomsthroughwhatseemstobeaconcretesurface`
3. `causalitySafenetLunaHSM111100x736B6E616220726F662074756F6C69616220646E6F63657320666F206B6E697262206E6F20726F6C6C65636E61684320393030322F6E614A2F33302073656D695420656854B5KR/1r5B/2R5/2b1p1p1/2P1k1P1/1p2P2p/1P2P2P/3N1N2 b - - 0 1`
4. `jacquefrescogiveitjustonesecondheisenbergsuncertaintyprinciple`

### Decoded Messages
- Phase 3 reveals a philosophical message about the nature of the puzzle
- Warning that the final phase involves 23+ ciphers, 16 encryptions, and 7 intertwined passwords
- Message about using the prize money wisely

## Current Status
✅ Repository cloned and ready
✅ All hints documented
✅ Images available for analysis
⚠️ Puzzle is still unsolved (private key not yet found)

## Next Steps for Puzzle Solvers
1. Review all phases in the README
2. Work through encrypted content systematically
3. Pay attention to Matrix movie references
4. Use the provided cipher tools
5. Consider the philosophical hints about resource allocation

## Additional Notes
- The puzzle creator suggests using funds wisely if found
- References to building something meaningful rather than just hunting prizes
- Multiple layers of encryption requiring patience and persistence
- Community discussions available on Reddit: r/bitcoinpuzzles

## Support the Repository
If you find this useful, consider donating BTC to: `1JK27jtvE1wS4VG9k7Zpo8wBufMbYwy3r8`

---
*Setup completed on 2025-10-30*
*Repository: https://github.com/puzzlehunt/gsmgio-5btc-puzzle*
