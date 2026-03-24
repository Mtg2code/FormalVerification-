# ECS324

## Tools Required
- Yosys
- ABC

## What I have learnt: 

### Q1 - Equivalence Checking
```
cd q1_equivalence
yosys equiv.ys
```
Checks whether ref and impl are sequentially equivalent.
Expected result: UNSAT (circuits are equivalent)

### Q2 - Safety Property (BMC)
```
cd q2_safety
yosys safety.ys
abc -c "read_aiger counter.aig; bmc -F 5"
```
Checks that counter never reaches state 11.
Expected result: SAT (violation found at step 3)

### Q3 - Liveness Property
```
cd q3_liveness
yosys liveness.ys
abc -c "read_aiger counter_live.aig; bmc -F 10"
```
Checks that counter eventually returns to 00.
Expected result: Cover condition reached (witness found)

### Q4 - Optimization and Equivalence Check
```
cd q4_optimization
yosys optimize.ys
yosys equiv_check.ys
```
Step 1: Optimizes the design and writes opt.v
Step 2: Checks that opt.v is equivalent to original design.v
Expected result: UNSAT (equivalent)
