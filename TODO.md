# Network Modifications

**Activation Function**
- integrate activation function in neurons.


**Astrocyte Energy Regeneration**

- accumulation rate
  - Option to regenerate as wave function over time.
- if it’s too high, they would never run out
- if it’s too low, the signals would still die out
- modify astrocyte initialized energy (currently set at max).
  - random between min and max provided values

**Threshold**

- each neuron has to receive a certain # of signals to fire = 3
- doesn’t mean exactly 3 signals were received, just that build up of signals/energy sums to 3
- non-negative value that stores # of signals received
  - subtracts 0.1 from # every iteration (decays at a constant rate)
    - adds 1 if a signal is received (enough to outweigh decay)
      - when it hits a total it will fire

- refractory period = 2 time steps	

```
m ← max(m + signals(now) - 0.1, 0) // decay cannot make value less than 0
if m >= 3 && enough time has passed // refractory period
	then
		m ← 0
		signal
```

- should result in less signals
- calculate average signals received per neuron
  - playing with threshold & refractory period

**Weights**

- Human Like Connectivity
  - neuron randomly chooses their number of connections from a power-law distribution.
    - few neurons have many connections, most neurons have few connections.
    - what happens to max distance allowed for connection?
  - graphical interface allowing to specify the distribution.
  - make connectivity look like human brain connectivity matrices.
  - primary sensory inputs, motor (decision) outputs.  

- add weight to Connection object
  - modify above to
    - mi ← max(mi + SUM0,connections.length(wi*signalsi(now)) - 0.1, 0)

    - create another array in neuron object to keep track of incoming signal connections ?
	
- initialization
  - eventually: interaction of weight and distance between neurons
  - eventually: bell curve probability of weights 
- 0-5-10 probability increases - higher at 5 then 0 and 10

**Inhibitors**

- 20% of neurons are inhibitors
- inhibitors can have a larger weight value than excitatory
  - 0-p of positive and 0-n of negative and possibly modify these values
- neuron has boolean: inhibitor true/false
  -eventually: colorful difference between inhibitory and excitatory signals

**STDP**

- implement Spike-timing dependent plasticity, and a learning task. -reinforcement-stdp?
- update connection weights, based on firing patterns.



