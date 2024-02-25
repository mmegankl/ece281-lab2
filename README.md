# Lab 2: Seven Segment Display Decoder

VHDL for ECE 281 [Lab 2](https://usafa-ece.github.io/ece281-book/lab/lab2.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Windows 11.

---

## Build the project

Follow the instructions to [Create a new Vivado Project](https://usafa-ece.github.io/ece281-book/appendix/vivado.html#create-a-new-vivado-project). Suggested name is binaryHexDisp.

Then add all the files in `src/hdl/` to the project, as described [here](https://usafa-ece.github.io/ece281-book/appendix/vivado.html#manually-add-files-to-vivado-project)

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/hdl/`.

Then it **elaborates** the *any* entity with the name `*_tb`. In this case, that is `helloled_tb`.

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.

Documentation Statement:
On 2/23, I met with Lt Col Trimble for EI to help with fixing the syntax, logic and other different areas with sevenSegDecoder.vhd and top_basys3_tb.vhd files. Additionally, on 2/24, C3C Wynn helped me with the following: helped me understand K-Maps better, helped fix my signals in the sevenSegDecoder, and added the rest of the annodes in the concurrent statements of the top_basys3.vhd file. From there, I was able to fix my equations in the prelab and fix my logic.
