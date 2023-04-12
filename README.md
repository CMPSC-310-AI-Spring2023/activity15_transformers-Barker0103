[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/ymop5HUw)
# CMPSC 310 Activity 15

## Deadline: April 12 by 9:50am

## Assignment

 For this activity follow [Neural machine translation with a Transformer and Keras](https://www.tensorflow.org/text/tutorials/transformer).

## Submission

Submit completed Colab notebook showing generated output.

# Data
The data that was used in this activity are sentences that are in English and Portuguese and they are all lowercase sentences, and the punctuation has spaces before and after it. After the data is downloaded, you have to tokenize it to be able to not get repeats and only get the essential information that you need. After that, the data is run through a pipeline function that puts the data into batches to get it ready to be trained and tested.

# Transformer Components

## The embedding and positional encoding layer
The positional encoding layer uses sines and cosines to calculate the positional encoding. The inputs to the encoder and decoder use the same positional encoding logic and it helps to identifty and put the words in the correct order.

## Add and Normalize
The add and normalize are spread out throught all of the components of the transformer model, and they are there so results can be run through a LayerNormalization layer. These blocks allow training to be more efficient and ensures that vectors are updated by the attention layers and not replaced.

## Base Attention Layer
The base attention layer has two inputs(the query sentence, and the context sentence). The base attention layer combines the values based on how well the query matches each key.

## The Cross Attention Layer
This layer connects the encoder and the decoder, and it takes information from the input sequence and gives it to the decoder so that it can predict the next output sequence token. It then takes the tokens and repeats this process until it can create and EOS token.

## The Global Self Attention Layer
This layer is responsible for processing the context sequence and growing information along its length. It allows every sequence element to access every other sequence elemtn and all the outputs to be computed in parallel.

## The Casual Self Attention Layer
This layer is similar to the global self attention layer but it needs to be handeled differently. It lets you compute loss for every locatoin in the output sequence while executing the model only once, and it also allows you to only need to calculate its outputs for each new token generated(the outputs for the previous sequence elements can be reused).

## The Feed Forward Network
In this network, the information moves from the input nodes through the hidden nodes if there are any and then to the output nodes.

## The Encoder Layer and the Encoder
The encoder layer contains a global self attention layer and a feedforward layer. The actual encoder has the a positional embedding layer that is added at the input.

## The Decoder Layer and the Decoder
The decoder layer is more complex and has a decoderlayer that contains a casual self attention, a cross attention, and a feed forward layer. The decoder is similar to the encoder where the only thing that is added is a positional embedding layer at the input.

## The Transformer
To complete the transformer model, you have to combine the encoder and the decoder and add a dense layer that converts the vector at each location into output token probabilities.