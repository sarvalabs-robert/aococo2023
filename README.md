# Advent of Coco 2024

A year after the first attempt to do Advent of Code in Coco programming language, here come the new examples. Now with Coco compiler v0.6.0 that supports packages, and has integrated execution of PISA code, programming and running the code got much easier. And using Advent of Code to find compiler bugs is still very much the main aim of this exercise.

The code can be run with
```
coco test --debug_pisa
```
as the correct results are parts of the test. So, the numbers are in `.coco` files, but the fun is getting to them by running the code.

# Day1
The results are already in the code, find the lines in `d01.coco`
```
// > distance: ...
// > similarity: ...
```

To run the code and see if the results are OK, do this:
```sh
cd AoCoco2024/01
coco test --debug_pisa
```

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
To invoke (=run) any function (endpoint) in Logiclab, a sender has to be designated. This is done only once. First start the logiclab with `logiclab start` and then issue two commands:
```sh
register TestUser
set designated.sender TestUser
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

# Day2
Both answers are in the same script, so:
```sh
cd 02
coco compile
logiclab run input1.lab | grep sum
```
