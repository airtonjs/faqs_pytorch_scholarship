﻿# Recurrent Neural Networks

**Q1: I found this lesson difficult to understand.  What additional resources are recommended?**

- At the beginning of the lesson Luis Serrano suggests these resources:
  
  Understanding LSTM Networks blogpost from [Chris Olah]( http://colah.github.io/posts/2015-08-Understanding-LSTMs/)
  
  Exporing LSTMs blogpost from [Edwin Chen]( http://blog.echen.me/2017/05/30/exploring-lstms/)
  
  The  Unreasonable  Effectiveness  of  Recurrent  Neural  Networks  blogpost from [Andrej Karpathy]( http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
  
  Lecture on RNNs and LSTMs from Stanford University’s CS231by [Andrej Karpathy]( https://www.youtube.com/watch?v=iX5V1WpxxkY)

- From @Vlad:

[LSTMs from Richard Socher and Stanford NLP]( https://youtu.be/QuELiw8tbx8) for mathematical but clean explanations.

**Q2: Please explain the significance of n_hidden in `nn.LSTM(input_size, n_hidden, n_layers, dropout=drop_prob, batch_first=True)`**
- Answered by @José Fernández Portal:

>n_hidden defines the size of your hidden state. The hidden state is a tensor that RNN outputs in every sequence step (t) and is the input for the next sequence step (t+1). In your diagram, it is represented by the right arrows. Basically, the hidden state carry information along the sequence. Regarding its size (n_hidden), I think that a bigger hidden state will allow to transfer more information along the sequence, but it becomes harder to train.

**Q3: Are there any resources to help in the understanding of LSTM batches and sequences?**
- Answered by @sundeep:

>A helpful [video](https://slack-files.com/T3Q738VV1-F4P1VE8SY-6f4e7770d0) from course instructor Mat.

A step-through of the sizes used in the Anna Karenina text character example may help in understanding how batches work [here](https://www.dropbox.com/s/417tcya72itbyz1/RNN_sizes.pdf?dl=0).

**Q4: In `get_batches` is there a more elegant way of creating `y`?** 
`Character_Level_RNN_Solution.ipynb`
``` 
# The targets, shifted by one
        y = np.zeros_like(x)
        try:
            y[:, :-1], y[:, -1] = x[:, 1:], arr[:, n+seq_length]
        except IndexError:
            y[:, :-1], y[:, -1] = x[:, 1:], arr[:, 0]
```
- Try the numpy command to roll array elements along an axis `numpy.roll(a, shift, axis=None)`
```
# The targets, shifted by one
        y = np.roll(x,-1)
```


