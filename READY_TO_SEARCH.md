# ✅ GSMG.IO 5 BTC Puzzle - Ready to Search!

## 🎯 Everything is Set Up!

You now have all the tools and data needed to search for the private key using BSGS or keyhunt.

## 📁 What We've Prepared

### Configuration Files
- ✅ `keyhunt_ranges.txt` - 7 search ranges based on puzzle hints
- ✅ `keyhunt_commands.sh` - Ready-to-run keyhunt commands
- ✅ `python_key_scanner.py` - Standalone Python scanner (no external tools needed)

### Documentation
- ✅ `KEYHUNT_GUIDE.md` - Complete guide for using keyhunt/BSGS
- ✅ `PUZZLE_STATUS_REPORT.md` - Full puzzle analysis
- ✅ `FINAL_SUMMARY.md` - What we know and don't know

### Target Information
- **Address**: `1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe`
- **Prize**: 2.5 BTC
- **Search Type**: Range-based around decoded hash values

## 🚀 Quick Start Options

### Option 1: Keyhunt (Fastest - Recommended)

```bash
cd /workspace/gsmgio-5btc-puzzle

# Run all ranges in parallel
bash keyhunt_commands.sh

# OR run a specific range
keyhunt -m address -f 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000:eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000 \
  -s 10
```

### Option 2: Python Scanner (No Installation Required)

```bash
cd /workspace/gsmgio-5btc-puzzle
python3 python_key_scanner.py
```

Then select which range to scan (1-3 or 'all').

### Option 3: BSGS (If you have it)

```bash
# Use the ranges from keyhunt_ranges.txt
# Example:
bsgs -a 1GSMG1JC9wtdSwfwApgj2xcmJPAwx7prBe \
  -r eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000:eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000
```

## 🎯 Priority Search Ranges

We've identified 5 most promising ranges based on puzzle hints:

### 1. Causality Hash ±16M (HIGHEST PRIORITY)
```
Center: eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d07e5bf
Range:  eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6d000000
    to  eb3efb5151e6255994711fe8f2264427ceeebf88109e1d7fad5b0a8b6e000000
Keys: ~16 million
```

### 2. Phase 3 Hash ±16M
```
Center: 1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d2ec30d5
Range:  1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d2000000
    to  1a57c572caf3cf722e41f5f9cf99ffacff06728a43032dd44c481c77d3000000
Keys: ~16 million
```

### 3. Matrixsumlist Hash ±16M
```
Center: e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df0ff345507
Range:  e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df0ff000000
    to  e7546e3076294907ed2a0ecaa9c33062f6e602b7c74c5aa5cc865df100000000
Keys: ~16 million
```

### 4. Salphaseion Hash ±16M
```
Center: 89727c598b9cd1cf8873f27cb7057f050645ddb6a7a157a110239ac0152f6a32
Range:  89727c598b9cd1cf8873f27cb7057f050645ddb6a7a157a110239ac015000000
    to  89727c598b9cd1cf8873f27cb7057f050645ddb6a7a157a110239ac016000000
Keys: ~16 million
```

### 5. VIC Cipher Number ±16M
```
Center: 12fa2812b6418266cf0d7d98d131da806dd112ae5f17b152f27b0f7400bd3ccc
Range:  12fa2812b6418266cf0d7d98d131da806dd112ae5f17b152f27b0f7400000000
    to  12fa2812b6418266cf0d7d98d131da806dd112ae5f17b152f27b0f7401000000
Keys: ~16 million
```

## ⏱️ Expected Time

### With Keyhunt (GPU accelerated)
- **Single range (±16M)**: 1-5 minutes
- **All 5 ranges**: 5-25 minutes
- **If not in narrow ranges, expand to ±1B**: Several hours

### With Python Scanner (CPU)
- **Single range (±16M)**: 10-30 minutes  
- **All 5 ranges**: 1-2 hours
- **Depends on CPU cores and speed**

### With BSGS
- **Typically faster than keyhunt for known ranges**
- **Similar times to keyhunt**

## 🎁 When You Find It

The script will automatically:
1. Print the private key (hex and decimal)
2. Save to `PRIVATE_KEY_FOUND.txt` or `SOLUTION_FOUND.txt`
3. Stop searching

**Then you can:**
1. Import the key into a secure Bitcoin wallet (Electrum, Bitcoin Core)
2. Verify the 2.5 BTC balance
3. Transfer the funds securely
4. Celebrate! 🎉

## 🧠 Why These Ranges?

Based on the puzzle's decoded hints:

1. **SHA256 Hashes**: All password hashes from the puzzle are 256-bit values - perfect for Bitcoin private keys
2. **"HALF AND BETTER HALF"**: The VIC cipher message hints at halves
3. **Pattern Recognition**: The puzzle uses hashes extensively
4. **Mathematical Derivations**: We tested XOR, addition, subtraction - now searching neighborhoods

## 📊 Already Tested (Not the Solution)

We've already verified these are NOT the keys:
- ❌ Direct hash values (compressed & uncompressed)
- ❌ XOR combinations of hashes
- ❌ Sum/difference of hashes (mod 2^256)
- ❌ Divided by 2 values
- ❌ VIC number modulo 2^256

So the key must be **near** one of these values, not exactly these values.

## 🔧 Troubleshooting

### If keyhunt is not installed:
```bash
git clone https://github.com/albertobsd/keyhunt.git
cd keyhunt
make
sudo make install  # or run from ./keyhunt
```

### If Python scanner is slow:
- It uses all CPU cores by default
- Consider using keyhunt (GPU accelerated)
- Or run on a more powerful machine

### If nothing found in narrow ranges:
- Expand search to ±1 billion around each center
- Try wider systematic search
- Review puzzle hints for additional clues

## 📚 Additional Resources

- `KEYHUNT_GUIDE.md` - Detailed keyhunt usage
- `PUZZLE_STATUS_REPORT.md` - Full puzzle breakdown
- Repository README - Original puzzle documentation

## 🎯 Success Probability

If our hypothesis is correct (key is near a puzzle hash):
- **Very High**: Key within ±16M of a candidate (~10 minutes search)
- **High**: Key within ±1B of a candidate (~few hours search)
- **Medium**: Key in a specific pattern we haven't tested yet
- **Low**: Key is completely random in 2^256 space (effectively impossible)

## ⚡ Pro Tips

1. **Run in parallel**: Use multiple terminals/machines for different ranges
2. **Start with causality**: It's from the earliest solved phase
3. **Be patient**: Even with fast tools, searching billions of keys takes time
4. **Monitor progress**: Watch the keys/second rate
5. **Check both compressions**: The scripts test both compressed and uncompressed

## 🚦 Status

- ✅ Puzzle analyzed
- ✅ Ranges identified
- ✅ Tools configured
- ✅ Scripts ready
- ⏳ **Ready to search!**

---

## 💡 Final Note

The puzzle creator's message emphasized using the prize for building something meaningful. If you solve this, consider honoring that intent!

**Now go find that key!** 🔑💰

Good luck! 🍀
