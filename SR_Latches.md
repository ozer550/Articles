# How is SR Latch a *Sequential circuit*

Lets try to first understand ,what actually is sequential circuit. Basically a circuit can be of two types 

* Combinational circuit
* Sequential circuit

## Combinational Circuits

A combinational circuit's outputs depend only on the current values of the input i.e it combines the current input values to compute the output values.

![Image of Combinational circuit](images/combinational_circuit.jpg)

This is a combinational circuit as the output completely depend upon the input values.

## Sequential Circuits

A sequential circuits outputs depend on both current and previous value values of inputs i.e it depends upon the input sequence .

Lets study the most common and easy sequential circuit called SR Latch and observe how the outputs of a sequentail circuits are dependent upon its current and previous inputs.

## SR Latch

![Image of Combinational circuit](images/SR_latch.jpg)

This circuit is called A SR Latch ,its one of the simplest sequential circuit consisting of two cross-coupled NOR gates. The latch has two inputs S and R and has two outputs Q and Q' . Lets try to figure out the four possible combinations of R and S. 

**Let the gate having  input R be named N1 and that having S be N2.**

* ### *case1 R=1 S=0* :

    Clearly when R is asserted the output of N1 will be 0 and that of N2 will be 1 .

* ### *case2 R=0 S=1* :

    when S is asserted  N2 gives a 0 output and N1 gives 1

* ### *case3 R=1 S=1* :

    As both the inputs have atleast one asserted input both gates give out a 0.

* ### *case2 R=0 S=0* :

    This is where the fun begins N1 recieves inputs of 0 and Q'. Because we dont yet know Q', we cant determine the output. Now similarily N2 recieves inputs of 0 and Q, But we dont know what Q is. Now we are stuck .

    But lets think a little deep we know that Q must be either 1 or 0 . So lets try to observe the subcases:-

    (At the given point the value of Q can be either 1 or 0 considering both cases )

    * #### *case1 Q=0* :
        As Q is false the N2 gate recieves both the inputs as 0 and hence spits out 1 

    * #### *case2 Q=1* :
         Now exactly inverse is happeningi i.e  N2 produces a false output and N1 recieves two false inputs spiting out true output

Now at this point we can get essence of what a sequential circuit is and how it is dependent on previous input , U might be thinking wait a minute isn't it same like a combinational circuit it all depends on S and R just the inputs, yes it untill the very point when both S and R become false i.e 0 ,as we discussed above the value of Q must be either 0 or 1 there's no other possiblity other than that ,then **what exactly decides the value of Q ?** and the answer is the previous state of the system whether it was in (set) i.e S=1 R=0 or S=0 R=1(reset) state the system gets the previous value of Q that is bieng decided by the previous inputs and hence it is called a sequential circuit.



