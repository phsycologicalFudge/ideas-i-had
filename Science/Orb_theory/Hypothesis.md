## Worm Orb Theory

*A basic theory and implementation plan for a C. elegans based artificial nervous system…not that I'll ever do it*

### 1. The foundational idea

The starting point is a mapped nervous system of C. elegans, available online. The biological connectome provides a 'network' structure. The question is whether that structure can be simulated, observed over time and converted into a richer artifact.

The foundational flow would essentially be:

*Biology -> simulation -> snapshots -> ML interpretation -> orb neurons -> artificial nervous system*

The mapped worm is the input, while the enriched artificial nervous system is the output. Machine learning serves as a transformation step, which in theory, converts the observed snapshots into a stable artifact (orb).

### 2. The orb neuron

Each artificial neuron is represented as an orb. Unlike a normal artifical nueron, an orb is not just a weight, but rather it is a structured object that preserves neuron identity while carrying information built from the simulated history of the original artifact.

To understand the artificial artifact, the core equation is:

*O_i = (T_i, H_i, R_i, W_i)*

*Orb i consists of identity, history, response profile, and weights.*

#### T_i: identity or role

T_i in this equation identifies what the neuron is in the mapped worm: its known name, broad role (sensory, motor), and any other labels extractable from the connectome or reference data. T_i was introduced because the same activity pattern can signify different things in different neuron classes.

#### W_i: connection weights

W_i holds the strength of the artificial neuron's connections. Initial values come from known connectivity and synapse data, then change during simulation if learning is enabled (which is reccomended by default).

#### H_i: history

H_i is likely the peak of this theory as it does not exist in a static connectome. Instead, it is created by running the artificial worm through time. History records how the neuron changed across many simulated situations. For example, the effects on environmental changes.

A useful equation would be:

*H_i = [S_i(t_1), S_i(t_2), ..., S_i(t_n)]*

*In short, history is built from repeated observations of neuron i over time.*

#### R_i: response profile

R_i is a crutial part of the equation, as it describes how the neuron tends to respond. Think of it as the neuron's personality in a broad sense. It is inferred from the neuron's history. The same input can produce different responses depending on T_i, past behaviour, environmental changes and more plausible constants. Although, these are the three i have identified as plausible.

A useful equation for this would be:

*R_i = f(T_i, H_i, E)*

*Response profile is inferred from identity, history, and environmental context.*

### 3. Why do snapshots matter?

The connectome is static by design, which introduces the main issue. Intelligence and behaviour are dynamic. To build history, the worm must first run as a 'best case' simulation. The simulator advances the nervous system through time while the environment changes and the worm acts inside it.

A useful equation for this would be:

*B_1, B_2, B_3, ..., B_n*

*Each B is a snapshot of the complete artificial brain at a different point in time.*

A long simulation could produce hundreds or thousands of snapshots. Each snapshot should, in theory, contain neural and environmental information so later analysis can separate correlation from context.

### 4. Artificial environment and evolution

A near perfect result will require the environment to react to the worm in real time. Food can regrow or collapse if consumption outpaces production. Temperature, hazards, resources, and other conditions change over time… so, random variation creates branches from the same initial era.

A useful equation for this would be:

*E_(t+1) = F(E_t, W_t, U_t)*

*The next environment depends on the current environment, worm behaviour, and random variation.*

The result is a simplified artificial ecosystem, which i suppose is dependant on the technological limits of said ecosystem. However, basic research has led me to beleieve that with mid to advanced programming skills, such an emulation is possible.

#### General Inheritance

A limit ai quickly discovered was the realistic lifespan expectation of C. elegans. Simulating a never ending lifespan almost defeats the very purpose of evolution, so the simulation must allow self-fertilisation, making a single simulated lineage practical. A descendant should not inherit the parent's full memory however, instead, inherited shift in weights are derived from the parent's learned changes.

A useful equation would be:

*W_child = W_base + ε * ΔW_parent*

*The child starts near the biological baseline, with a small inherited bias from the parent. While inperfect, it is the solution I think is realistic.*

Two timescales emerge as a positive consequence: learning during one lifetime and evolutionary drift across generations. If the lineage eventually diverges so far that it is no longer meaningfully C. elegans, that is not a failure. Instead, it is an emergent descendant of the original architecture.

### 5. Machine learning role

The ML's job is simple. To read the mapped, biological nueron data and snapshots, and converge on a mathematically probably representative. That is, the orb neuron.

The useful equation for this:

*(T_i, W_i, H_i, E) -> ML -> O_i*

This does of course assume the orb nueron produces greater results than a simple weighted model.

### 6. The basic implementation plan

There are nine distinct stages as of the date of this hypothesis.

- Phase 1: obtain and understand the labelled C. elegans connectome.
- Phase 2: encode the 302-neuron network and its connections.
- Phase 3: create a simple environment with movement, food, hazards, and changing conditions.
- Phase 4: run the network through time and log complete brain snapshots.
- Phase 5: add limited lifetime weight adaptation.
- Phase 6: add generations with small inherited weight bias.
- Phase 7: manually inspect neuron histories and define the first response features.
- Phase 8: train a small ML system to convert identity, history, response, and weights into orb representations.
- Phase 9: compare the original network and orb network under the same environments.

### 7. Symbols in use

| Symbol | Meaning | Plain English |
|---|---|---|
| i, j | Neuron indices | Neuron i, neuron j |
| O_i | Orb representation of neuron i | The enriched artificial neuron |
| T_i | Identity or role | What kind of neuron it is |
| W_i | Weights | Strength of its connections |
| H_i | History | How it changed over time |
| R_i | Response profile | How it tends to react |
| E_t | Environment at time t | What the world looks like now |
| B_t | Brain snapshot at time t | The whole artificial brain at one moment |
| t | Time | Current simulation time |
| Δ | Change in a value | e.g. ΔW = change in weights |
| ε | Small inheritance factor | How much parental weight change passes on |
| f(...) | A function or process | Some rule that converts inputs into an output |
| F(...) | Environment update function | The rules that change the world |
| -> | Transformation or flow | One stage leads into another |
| = | Equality or definition | Left side is defined by the right side |
| U_t | Random variation at time t | Unpredictable change affecting the environment |

### 8. Current hypothesis & degeneracy

A biological neural network may become more adaptive if each neuron is represented by a richer object. The original idea was based on AGI, however this simpler model is the first step to understanding AGI.

The value of O_i may lie in the combined state that produces a more complex instruction. A smaller underlying theory of mine: instruction_1 + instruction_2 = x, where i1 and i2 could themselves be composites like i1(w1 + w2 + w3) or i1(w1 + r1 + r2).

Consider a coat that is pink. Then a second coat that is red and white mixed to make the same pink. Both are equally pink, arrived with different compositions through complexity. Now a third coat: red and white with smaller additions of blue and white. The result is a slightly different shade of pink, still pink, still serving its original purpose, just much richer in its composition. Carried into this theory, that richer composition means theoretically richer in effect.

Both coats produce the same pink under normal conditions. The difference only shows up when something unexpected happens in practice. If the environment shifts, or a new input appears that neither composition has seen before, the simpler coat (pure pink) has nothing to fall back on. The richer coat (red, white, blue, white) has more internal variation to draw from, which in theory means it adapts better. So the argument for the orb model over a weight-only model is not really about day to day performance (albeit that does matter in the general sense), but that it should hold better when outside circumstances change substantially within natural bounds.

### 8.1 Identity drift

A crutial part of this hypothesis is the identity of the final artifact. If you can still trace back to the original worm even after learning and generational changes have accumulated, then the test has succeded.
