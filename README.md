# Polars Resources
- [Ruby Polars Repo/Docs](https://github.com/ankane/polars-ruby)
- [Polars API reference](https://pola-rs.github.io/polars/py-polars/html/reference/index.html)
- [Vega](https://github.com/ankane/vega-ruby) -- Graphing library to use with Polars

## Social Communities
- [X Ruby AI group](https://twitter.com/i/communities/1709211359039078677)
- [Mastodon Ruby AI and Data group](https://ruby.social/@Ruby_AI_and_Data@chirp.social)

## Machine Learning/AI
- [Awesome Machine Learning with Ruby repo](https://github.com/arbox/machine-learning-with-ruby)
- [Andrew Kane's ML Gems](https://ankane.org/new-ml-gems)
- Landon Gray's [introduction to Machine Learning with Ruby](https://www.youtube.com/watch?v=656z7Hu0HtY&list=PLbHJudTY1K0cOM1jfOsQLYPTLxQf1Ui1C&index=8&pp=iAQB
)
- Justin Bowen's [Discover Machine Learning in Ruby](https://www.youtube.com/watch?v=XXtqUptI_oQ&list=PLbHJudTY1K0dERpqJUEFOFSsMGvR6st9U&index=49)
- Machine learning Docker images for Ruby [ml-stack](https://github.com/ankane/ml-stack)
- [Rumale](https://github.com/yoshoku/rumale) (Ruby machine learning) is a machine learning library in Ruby. Rumale provides machine learning algorithms with interfaces similar to Scikit-Learn in Python.
- [ONNX Runtime Ruby](https://github.com/ankane/onnxruntime-ruby) high performance scoring engine for ML models - for Ruby
### Deep Learning
- [Torch.rb](https://github.com/ankane/torch.rb) and [TensorFlow](https://github.com/ankane/tensorflow-ruby)
- [TorchVision](https://github.com/ankane/torchvision-ruby) for computer vision tasks
- [TorchText](https://github.com/ankane/torchtext-ruby) for text and NLP tasks
- [TorchAudio](https://github.com/ankane/torchaudio-ruby) for audio tasks
- [TorchRec](torchrec-ruby) for recommendations 

### Forecasting
- [Prophet.rb](https://github.com/ankane/prophet-ruby) is a forecasting library. It supports multiple seasonalities, holidays, growth caps, and many other features.
- [MITIE](https://github.com/ankane/mitie-ruby) does named-entity recognition. It finds people, organizations, and locations in text.

## Other DataFrame Gems
- [Daru](https://github.com/SciRuby/daru)
- [Rover](https://github.com/ankane/rover)
- [RedAmber](https://github.com/red-data-tools/red_amber)

## Jupyter Notebook
- [IRuby](https://github.com/SciRuby/iruby)
- [Jupyter](https://docs.jupyter.org/en/latest/install.html)
- [Google Colab](https://colab.google/)
- Host Jupyter Notebooks online [mybinder](https://mybinder.org/)

## N-dimensional Array Gems
- [Numo::NArray](https://github.com/ruby-numo/numo-narray)
- [NMatrix](https://github.com/SciRuby/nmatrix)

## Misc

- [SciRuby](https://github.com/SciRuby)
- [Outlier Detection and Removal](https://medium.com/analytics-vidhya/removing-outliers-understanding-how-and-what-behind-the-magic-18a78ab480ff) Though in Python it's a good high level introduction to the statistical concepts. Introduces you to IQR and Standard Deviation, the two main outlier removal types.
```Ruby

# Std Deviation - filtering 2 std deviations away
df = Polars::DataFrame.new({'example' => [10, 20, 30, 40, 50, 10000]})
mean = df['example'].mean
std = df['example'].std
outliers = (df['example'] < mean + (2 * std)) & (df['example'] > mean - (2 * std))
removed = df.filter(outliers)

#one liner
removed = df.filter((df['example'] < df['example'].mean + (2 * df['example'].std)) & (df['example'] > df['example'].mean - (2 * df['example'].std)))

#IQR
series = Polars::Series.new('example', [-2.08,  1.9, -5.70, 7.08,  0.73, -3.50, 2.57,  0.21, -9.26])
series.quantile(0.75, interpolation:"nearest")
```
