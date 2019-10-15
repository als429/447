# Gates and Wires

* Circuits we use to implement, the hardware
* What's electricity?
  * protons can't move, electrons can
  * opposites attract
  * squeezing electrons together, they don't want to be together
      * closer you squeeze together, they're less happy :-(  
  * give them a really difficult path out 
  * battery - something that squeezes elections
  * electron shuffle (distance they move = small); but they bump into each other
  * voltage = electron unhappiness
      * higher = more squished
   * current
      * measure of how many electrongs per second are moving past a point
    
 ## Gates
 
* Transitor is like a little value or switch
* input, output, and a control are all single bits
* the bits are represented as voltages 
  * connects its inputs to its output if control is a 1
* we combine transistors in interesting ways to make **gates**
* a gate implements one of the basic boolean logic functions

### NOT gate
* like a sideways girl
* bubble/ head means NOT

### AND gate
* like a D
* round at the end
* A AND 0 = just use 0
* A AND 1 = just use A


### OR gate
* pointed end
* A OR 1 = just use 1
* A OR 0 = just use A

### XOR gate
* exactly one is true (soup or salad)
* pointed
* line before
* not used in practice, like AND, OR, and NOT
* A XOR 0 = just use A
* A XOR 1 = just use not A

### Constants
* You should never have a gate with a constant input

### NAND gate
* NOT AND
* opposite of AND
* D with circle (not) on end
* fastest kind of gate to manufacture
* it is universal
* not can making anything with a NAND gate
* you can build entire circuits
* how they used to build computers


## Logical +
* + = OR = logical sum
* no space = AND

## Logisim's wire colors
* organizes wires according to their kind and state
* green wire = 1-bit
* blue wire = carrying X (not one or zero; avoid these) 
 * when you don't hook up wire to anything
 * wire is floating
* red wire = error
 * fix the bug
* organge wire = size mismatch
 * you have a different bug
 * two things of different bit widths connected together
* black wires = shorthand wire bundles


# Splitters
* How we convert between bundles and individual wires
* get multiple smaller values
* what hairbrush looking thing is doing
* can also braid bad together

# When designing circuits
* a wire can have one output connected
 * and any number connected inputs
* tunnel connects wires across distances (NAMED WIRES -> adding [label])
 * the name of the tunnel is what's important.
 * any tunnels of the same name are "virtually" connected
 * give a name to a wire
* can have spaghetti circuits, they actually look like it


 
