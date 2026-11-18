
# Main

Basically we know the backpropagation algorithm, but let's explore by the layers types
    - Linear
    - Embeddings
    - FA  (Functions activations)
    - Norms
    - And more



# Backpropagation in Simple Words

## Forward pass

A neural network is basically a big function: it receives an input, passes it through a sequence of layers and produces an output. This process is called the **forward pass**.

```
input → layer 1 → layer 2 → ... → layer N → output → loss
```

At the end, a **loss** function compares the output with the expected answer and tells us how wrong the model was.

## Backward pass (backpropagation)

For the model to learn, we need to know **how much each weight contributed to the error**, and in which direction it should change to reduce it. That is what backpropagation computes.

Backpropagation is not an "inverse function". It uses the **derivatives** of every layer, combined through the **chain rule**, to compute the **gradient** of the loss with respect to every weight.

In the forward pass, the signal goes from the start to the end. In the backward pass, the **gradient** travels in the opposite direction, from the loss back to the first layer.

```
Forward:   input → layer 1 → layer 2 → layer 3 → loss
Backward:  input ← layer 1 ← layer 2 ← layer 3 ← loss
```

## The chain rule

Since the layers are chained one after another, the effect of an early weight on the loss is the **product** of the local derivatives along the way:

```
dL/dw1 = dL/dy3 · dy3/dy2 · dy2/dy1 · dy1/dw1
```

Each layer only needs to know its own local derivative. The rest comes from the layers after it.

## What happens in each layer

During the backward pass, every layer does three things:

1. **Receives** the gradient coming from the layer after it (how much the loss changes when this layer's output changes).
2. **Computes the gradient of its own weights**, which the optimizer will use to update them.
3. **Passes** the gradient with respect to its input to the layer before it.

To compute these gradients, each layer reuses values saved during the forward pass (the activations). This is why training uses much more memory than inference.


# Layers

## Linears

## Embeddings

### RoPE

## Function Activations

### Sigmoid

### Softmax

### RELU

## Normalizations


## Attention Layers

### MHA

### GQA

### MQA

## Blocos de regularização

### Dropout

### Clipping
