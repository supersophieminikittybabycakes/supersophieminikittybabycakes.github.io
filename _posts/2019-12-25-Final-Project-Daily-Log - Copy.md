---
layout: post
Title: Final Project: German Translator
---



For our final project in Machine Learning, we created a translator using PyTorch and torchtext neural networks. Before deciding on the specific topic for our project, we decided that we just wanted to learn about neural networks and pick a particular application afterward. From our preliminary research, we learned that neural networks are algorithms that use pattern recognition to interpret data by clustering it or labeling it. After our research, we thought that translation would be a pretty cool application of neural networks. Our launching pad for this project was [this article](https://pytorch.org/tutorials/beginner/torchtext_translation_tutorial.html?highlight=transformer) that we found on the PyTorch website. 
Our project was not exactly a culmination of our work over the semester. Rather, it was an extension of the natural language processing unit combined with a little research about neural networks. We learned that the first step of language translation is tokenization. Tokenization is the splitting up of the sentences into smaller pieces that are easier to process. We determined that the SpaCy package was the best tokenizer for us to use because it has options for many different languages. However, getting the appropriately updated version of SpaCy took a few tries and some confusing errors to get past. After getting SpaCy, we used the article as an example to build our neural network from. After some debugging, the network ran smoothly without error which was a relief considering the difficulty of downloading all the required packages (torch, SpaCy, etc.). We also decided that we wanted to translate between English and German (because why the hell not?!).
When thinking back on how our model functions (and neural networks in general), we had to do some reading back of our code and internet digging. I think we still have merely a basic understanding of the whole thing, but basically our preprocessing splits up the words and BucketIterator turns the sentences into tensors for source and target languages. Then, we pass the tensors through the neural network and creates the model. Our neural network architecture of a decoding network passed into an encoding network which also uses an attention network to encode. Essentially, decoding is the equivalent of reading and encoding is the equivalent of comprehending. 
But, there’s no easy command to use the model on a single sentence. We have to pass in a source tensor version of whatever sentence we want. It’s easier to pull off a tensor from the dataset, and a little harder to convert sentence to tensor, put it through the model, and reinterpret the output tensor. The tutorial code that we reproduced only had an output of the various values for the model’s training/testing loss. While the training and testing loss is good information to have, it really didn’t give us a tangible means of exploring what our translator could do. The next challenge was building a function that would actually convert one language into another.
To achieve this objective, we constructed a helper function that coverts tensor into a sentence. We were able to successfully translate an English sentence into a vector and back to an English sentence. And we were able to successfully translate a German sentence to a vector and back to a German sentence. But we still struggled with translating from one language to a vector to another language. 
After a long period of being stuck, a helpful coder (Sophie’s dad) figured out that instead of passing in a target tensor of 0, the target tensor has to have big enough dimensions to basically engulf the source tensor. We initially had a target tensor vector of just one zero. Essentially, with an empty target tensor, the model cannot change the source tensor into an output because the target tensor for comparison and the source tensor are too dissimilar in shape. We sideskirted this error by passing in the target tensor as  “the the the the the the the.” Although this target tensor is obviously nothing close to what the final translation is going to be, it is at least large enough for the model to be able compare the target and source tensors and create an output. Using a few helper functions (thanks Lauren), we were able to take a single sentence and get a sort of legitimate prediction for the translation, whereas before we were unable to get anything other than a a aa a a before.


Real English Translation: two young , white males are outside near many bushes


! [Oops! This image cannot be loaded.](/images/photo1)


Well, that’s not too bad


Real English translation: It’s unbelievable how much this cost


! [Oops! This image cannot be loaded.](/images/photo2)


Uh oh... very bad translation

Looking over the translations that our model gives, there’s a huge amount of variability. Simple phrases with numbers, colors, and nouns seem to be handled much better. Many words are interpreted as unknown, signifying that we need to bulk up the vocabularies for both languages. Additionally, it seems like each word of an input sentence is being translated one by one, or not taking into account the surrounding words. Improving these different facets of our model would be awesome... and adding more languages. But in the meantime, we should probably just use Google Translate for all our multilingual needs.
You can find our code at [here](https://github.com/supersophieminikittybabycakes/TorchText-Translator-Final-ML-Project-/blob/master/Copy_of_New_Translator.ipynb)