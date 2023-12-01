# Advent of Coco 2023

Here's an attempt to do https://adventofcode.com in Coco programming language (https://cocolang.dev).

It's unlikely this will be doable with anything complex, but having at least the first day completed, it's a proof Coco can work as a general programming language.

And of course, an excellent way to find Coco compiler bugs!

# Day1
If you're only interested in two numbers, install Coco 0.3.5 and run:
```sh
cd 01
coco compile
logiclab run input1.lab | grep calibration
logiclab run input2.lab | grep calibration
```

If you're interested in more details, read on!

# Running

Install Coco compiler, release 0.3.5 from https://cocolang.dev/releases

Results for Day1 are well, in the folder `01`. You need to initialize `logiclab` before first run (if there's not `./logiclab` folder).
```sh
cd 01
logiclab init
```

## Test
As Coco enables testing out-of-the box, the code includes tests from the exercise in the source code, so we can verify correctness. Default base fuel in `logiclab` is 10000, which is far too little for loops, so even the simplest test need higher fuel (1,000,000 is a good start).

```sh
coco labtest --fuel 1000000
```

## Exercise
First, we need to compile the code, `coco.nut` file determines the format and output file (`d01.yaml`)
```sh
coco compile
```

The real exercises require long inputs, as Coco can't read files, we have to provide the input as a long function argument. Luckily, `logiclab` can handle it. We need to set an even larger fuel limit as we did for the previous test, read and compile the manifest and invoke `Calibrate` or `Calibrate2` endpoints. All commands are written in `input1.lab` and `input2.lab` files, so we can just do
```
logiclab run input1.lab | grep calibration
logiclab run input2.lab | grep calibration
```
