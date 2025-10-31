# GSMG.IO 5 BTC Puzzle - Key Hunt/BSGS Guide

## 🎯 Target Information
- **Address**: `1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe`
- **Prize**: 2.5 BTC (~$100,000+)
- **Status**: Unclaimed

## 📊 Candidate Ranges for Search

Based on decoded puzzle hints, we have identified several promising search ranges:

### Priority Ranges (Most Likely)

#### 1. Causality Hash Range
- **Center**: `eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d07e5bf`
- **Decimal**: `106404798465797557723086389712955339454006600081500349604329604841312868623807`
- **Search**: ±16M around this value

#### 2. Phase 3 Hash Range
- **Center**: `1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d2ec30d5`
- **Decimal**: `11915212496638264002424045223256946618792705674248593069722361279985375523029`
- **Search**: ±16M around this value

#### 3. Matrixsumlist Hash Range
- **Center**: `e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df0ff345507`
- **Decimal**: `104633443674795341178004690833413099512518243364442002031249108298907776210183`
- **Search**: ±16M around this value

#### 4. Salphaseion Hash Range
- **Center**: `89727c598b9cd1cf8873f27cb7057f050645ddb6a7a157a110239ac0152f6a32`
- **Decimal**: `62169139051977406799456590670741406588888301705500207831609968087667150121522`
- **Search**: ±16M around this value

#### 5. VIC Cipher Number (mod 2^256)
- **Center**: `12fa2812b6418266cf0d7d98d131da806dd112ae5f17b152f27b0f7400bd3ccc`
- **Search**: ±16M around this value

## 🔧 Method 1: Using Keyhunt

### Installation
```bash
git clone https://github.com/albertobsd/keyhunt.git
cd keyhunt
make
```

### Commands

Run all ranges in parallel:
```bash
cd /workspace/gsmgio-5btc-puzzle
bash keyhunt_commands.sh
```

Or run individual ranges:

```bash
# Range 1: Causality
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000:eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000 \
  -s 10

# Range 2: Phase3
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r 1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d2000000:1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d3000000 \
  -s 10

# Range 3: Matrixsumlist
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df0ff000000:e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df100000000 \
  -s 10
```

### Keyhunt Options
- `-m address`: Search by address
- `-f <address>`: Target address to find
- `-r <start>:<end>`: Range to search (hex format)
- `-s <stride>`: Step size (higher = faster but might miss keys)
- `-t <threads>`: Number of threads (default: CPU cores)
- `-n <bits>`: For BSGS mode, specify bit range

### Advanced Keyhunt with BSGS
```bash
# If you have the public key (requires transaction history)
keyhunt -m bsgs -f <PUBLIC_KEY> -b <BITS> -n <RANGE>
```

## 🚀 Method 2: Using BSGS Tools

BSGS (Baby-step Giant-step) is faster if you have the public key.

### Get Public Key
First, check if the address has any outgoing transactions:
```bash
# Check blockchain explorer or use:
curl "https://blockchain.info/address/1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe?format=json"
```

### If Public Key is Available
```bash
# Example BSGS command (adjust based on your BSGS tool)
bsgs -p <PUBLIC_KEY_HEX> \
  -s eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000 \
  -e eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000
```

## 🐍 Method 3: Python Scanner (No External Tools)

We've created a Python scanner that runs on any system:

```bash
cd /workspace/gsmgio-5btc-puzzle
python3 python_key_scanner.py
```

Features:
- Multi-core parallel scanning
- Checks both compressed and uncompressed addresses
- Progress reporting
- Automatic solution saving

## 📈 Search Strategy

### Phase 1: Quick Scan (Hours)
Search narrow ranges (±16M) around each candidate:
- Causality hash ±16M
- Phase3 hash ±16M  
- Matrixsumlist hash ±16M

### Phase 2: Extended Scan (Days)
If Phase 1 fails, expand to ±1B around each candidate

### Phase 3: Wide Search (Weeks)
Search larger segments:
- Upper half of keyspace (2^255 to 2^256-1)
- Lower half (1 to 2^255-1)

### Phase 4: Systematic Combinations
Try mathematical combinations:
- XOR of hash pairs
- Addition/subtraction modulo 2^256
- Derived values from VIC cipher

## 🔑 Why These Ranges?

1. **Hash Values as Seeds**: The puzzle uses SHA256 hashes as passwords. These same hashes might be private keys.

2. **"HALF AND BETTER HALF" Hint**: Suggests looking in halves of the keyspace or half-values of known numbers.

3. **VIC Cipher Number**: The 152-digit number might encode the key directly.

4. **Pattern in Puzzle**: Previous phases used hex-encoded strings. The final key might follow this pattern.

## 📝 Files Created

- `keyhunt_ranges.txt` - Range specifications
- `keyhunt_commands.sh` - Bash script for parallel keyhunt
- `python_key_scanner.py` - Python-based scanner
- This guide (`KEYHUNT_GUIDE.md`)

## ⚠️ Important Notes

### Computational Requirements
- **Narrow ranges (±16M)**: ~32M keys per range, scannable in hours
- **Wide ranges (±1B)**: ~2B keys per range, requires days/weeks
- **Full range search**: Not feasible without specialized hardware

### Success Indicators
If the private key is found, the script will:
1. Print the key in both hex and decimal format
2. Save to `PRIVATE_KEY_FOUND.txt`
3. Stop all other workers

### Next Steps After Finding Key
1. **Import to wallet**: Use a secure Bitcoin wallet (Electrum, Bitcoin Core)
2. **Verify balance**: Check that address has 2.5 BTC
3. **Transfer safely**: Use proper OpSec, consider splitting funds
4. **Report ethically**: Consider contacting puzzle creator

## 🎲 Probability Analysis

**Best case scenario** (key is near one of our candidates):
- 5 ranges × 32M keys each = 160M total keys
- At 1M keys/second: ~160 seconds (3 minutes)
- At 100K keys/second: ~1,600 seconds (27 minutes)

**Realistic scenario** (key within ±1B of candidates):
- 5 ranges × 2B keys each = 10B total keys  
- At 1M keys/second: ~10,000 seconds (2.8 hours)
- At 100K keys/second: ~100,000 seconds (27 hours)

**Worst case** (random key in 2^256 space):
- Essentially impossible without quantum computing

## 🔄 Parallel Execution

To maximize speed, run multiple ranges simultaneously:

```bash
# Terminal 1
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000:eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000

# Terminal 2
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r 1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d2000000:1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d3000000

# Terminal 3
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df0ff000000:e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df100000000
```

## 📞 Support

If you find the key:
- Save it securely immediately
- Document your method
- Consider the puzzle creator's philosophical message about using funds wisely

---

**Good luck with the search! The key is out there waiting to be found.** 🔐
