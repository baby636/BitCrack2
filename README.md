# BitCrack2
_Hunt for Bitcoin private keys._

It is a modified version of [BitCrack](https://github.com/brichard19/BitCrack) by [brichard19](https://github.com/brichard19),
for random mode.

Thank you him for his hardwork.

## Note: It's a experimental project.
# Changes 

- Added random stride option, by using this option, the program run indefinitely after the end of keyspace, it starts again from starting range with the updated random stride of given bit length, it continues doing this until it found keys or you stoped it. This is like a random walk with random distance.
- In --rstride N, N should be ```64 >= N >= 1```
- Saving-Loading checkpoints are not modified for new changes.
- Everything else is same as original BitCrack.
  
# Usage

```
BitCrack.exe --help
BitCrack OPTIONS [TARGETS]
Where TARGETS is one or more addresses

--help                  Display this message
-c, --compressed        Use compressed points
-u, --uncompressed      Use Uncompressed points
--compression  MODE     Specify compression where MODE is
                          COMPRESSED or UNCOMPRESSED or BOTH
-d, --device ID         Use device ID
-b, --blocks N          N blocks
-t, --threads N         N threads per block
-p, --points N          N points per thread
-i, --in FILE           Read addresses from FILE, one per line
-o, --out FILE          Write keys to FILE
-f, --follow            Follow text output
--list-devices          List available devices
--keyspace KEYSPACE     Specify the keyspace:
                          START:END
                          START:+COUNT
                          START
                          :END
                          :+COUNT
                        Where START, END, COUNT are in hex format
--stride N              Increment by N keys at a time
--rstride N             Random stride bits, continue after end of range by setting up new random stride
--share M/N             Divide the keyspace into N equal shares, process the Mth share
--continue FILE         Save/load progress from FILE
-v, --version           Show version
```

For puzzle ```35```, ```36``` and ```37```
```
BitCrack.exe -b 64 -t 256 -p 1024 --rstride 5 --keyspace 400000000:1FFFFFFFFF 1PWCx5fovoEaoBowAvF5k91m2Xat9bMgwb 1Be2UF9NLfyLFbtm3TCbmuocc9N1Kduci1 14iXhn8bGajVWegZHJ18vJLHhntcpL4dex
[2021-07-14.17:01:04] [Info] Compression : compressed
[2021-07-14.17:01:04] [Info] Starting at : 400000000 (35 bit)
[2021-07-14.17:01:04] [Info] Ending at   : 1FFFFFFFFF (37 bit)
[2021-07-14.17:01:04] [Info] Range       : 1BFFFFFFFF (37 bit)
[2021-07-14.17:01:04] [Info] Initializing GeForce GTX 1650
[2021-07-14.17:01:04] [Info] Generating 16,777,216 starting points (640.0MB)
[2021-07-14.17:01:09] [Info] 10.0%  20.0%  30.0%  40.0%  50.0%  60.0%  70.0%  80.0%  90.0%  100.0%
[2021-07-14.17:01:11] [Info] Done
[DEV: GeForce GTX 1650 3334/4096MB] [K: 78E000000 (35 bit), C: 12.695313 %] [I: 1A (5 bit), 3] [T: 3] [S: 306.85 MK/s] [12,096,372,736 (34 bit)] [00:00:50]
[2021-07-14.17:02:05] [Info] Found key for address '1Be2UF9NLfyLFbtm3TCbmuocc9N1Kduci1'. Written to 'Found.txt'
[2021-07-14.17:02:05] [Info] Address     : 1Be2UF9NLfyLFbtm3TCbmuocc9N1Kduci1
                             Private key : 9DE820A7C
                             Compressed  : yes
                             Public key  : 02B3E772216695845FA9DDA419FB5DACA28154D8AA59EA302F05E916635E47B9F6

[DEV: GeForce GTX 1650 3334/4096MB] [K: 418000000 (35 bit), C: 0.334821 %] [I: 18 (5 bit), 12] [T: 2] [S: 30.74 MK/s] [57,327,747,072 (36 bit)] [00:04:13] 1]
[2021-07-14.17:05:31] [Info] Found key for address '1PWCx5fovoEaoBowAvF5k91m2Xat9bMgwb'. Written to 'Found.txt'
[2021-07-14.17:05:31] [Info] Address     : 1PWCx5fovoEaoBowAvF5k91m2Xat9bMgwb
                             Private key : 4AED21170
                             Compressed  : yes
                             Public key  : 02F6A8148A62320E149CB15C544FE8A25AB483A0095D2280D03B8A00A7FEADA13D

[DEV: GeForce GTX 1650 3334/4096MB] [K: 1497000000 (37 bit), C: 59.249442 %] [I: 1F (5 bit), 17] [T: 1] [S: 306.85 MK/s] [86,939,533,312 (37 bit)] [00:06:27]
[2021-07-14.17:07:41] [Info] Found key for address '14iXhn8bGajVWegZHJ18vJLHhntcpL4dex'. Written to 'Found.txt'
[2021-07-14.17:07:41] [Info] Address     : 14iXhn8bGajVWegZHJ18vJLHhntcpL4dex
                             Private key : 1757756A93
                             Compressed  : yes
                             Public key  : 027D2C03C3EF0AEC70F2C7E1E75454A5DFDD0E1ADEA670C1B3A4643C48AD0F1255


[2021-07-14.17:07:41] [Info] No targets remaining
```

# Building
### Windows
- Microsoft Visual Studio Community 2019
- CUDA version 10.0
## Linux
- Install libgmp: ```sudo apt install -y libgmp-dev```

- Edit the makefile and set up the appropriate CUDA SDK and compiler paths for nvcc.

    ```make
    CUDA       = /usr/local/cuda-11.0
    CXXCUDA    = /usr/bin/g++
    ```
 - To build with CUDA: pass CCAP value according to your GPU compute capability
    ```sh
    $ cd BitCrack
    $ make CCAP=75 all
    ```

# License
BitCrack is licensed under MIT License.


# __Disclaimer__
ALL THE CODES, PROGRAM AND INFORMATION ARE FOR EDUCATIONAL PURPOSES ONLY. USE IT AT YOUR OWN RISK. THE DEVELOPER WILL NOT BE RESPONSIBLE FOR ANY LOSS, DAMAGE OR CLAIM ARISING FROM USING THIS PROGRAM.