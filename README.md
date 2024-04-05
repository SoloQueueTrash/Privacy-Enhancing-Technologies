# trp_assig2

# Step #1 - Protocols for Private Set Intersection (PSI): Study, Description and Comparison

```
sudo apt install -y g++ make libgmp-dev libglib2.0-dev libssl-dev
git clone -recursive https://github.com/eduardo010174/PSI
cd PSI
make
```

* Follow: https://github.com/rscmendes/PSI#executing-the-code
* Test:
```
./demo.exe -r 0 -p 0 -f sample_sets/emails_alice.txt
./demo.exe -r 1 -p 0 -f sample_sets/emails_bob.txt
```
### Usage 

```
 -r [Role: 0/1, required]
 -p [PSI protocol (0: Naive, 1: TTP, 2: DH, 3: OT), required]
 -f [Input file, required]
 -a [Server IP-address (needed by both, client and server), optional]
 -n [Number of elements, optional]
 -t [Flag: Enable detailed timings, optional]

```
### Option -p
```
-p 0: the naive hashing protocol
-p 1: the server-aided protocol of [4]
-p 2: the Diffie-Hellman-based PSI protocol of [5]
-p 3: the OT-based PSI protocol of [3]
```

# Step #2 - Experimentation with Protocols for Private Set Intersection

# Step #3 - Benchmarking Private Set Intersection Protocols

# Step #4 - Apply secure intersection protocols to another dataset of your choice