# Polars Resources
- [Ruby Polars Repo/Docs](https://github.com/ankane/polars-ruby)
- [Polars API reference](https://pola-rs.github.io/polars/py-polars/html/reference/index.html)
- [Vega](https://github.com/ankane/vega-ruby) -- Graphing library to use with Polars

## Machine Learning/AI
- [Awesome Machine Learning with Ruby repo](https://github.com/arbox/machine-learning-with-ruby)
- [Andrew Kane's ML Gems](https://ankane.org/new-ml-gems)
- Landon Gray's [introduction to Machine Learning with Ruby](https://www.youtube.com/watch?v=656z7Hu0HtY&list=PLbHJudTY1K0cOM1jfOsQLYPTLxQf1Ui1C&index=8&pp=iAQB
)
- Justin Bowen's [Discover Machine Learning in Ruby](https://www.youtube.com/watch?v=XXtqUptI_oQ&list=PLbHJudTY1K0dERpqJUEFOFSsMGvR6st9U&index=49)
- Machine learning Docker images for Ruby [ml-stack](https://github.com/ankane/ml-stack)
- [Rumale](https://github.com/yoshoku/rumale) (Ruby machine learning) is a machine learning library in Ruby. Rumale provides machine learning algorithms with interfaces similar to Scikit-Learn in Python.
- [ONNX Runtime Ruby](https://github.com/ankane/onnxruntime-ruby) high performance scoring engine for ML models - for Ruby
- [X Ruby AI community](https://twitter.com/i/communities/1709211359039078677)
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
- [Outlier Detection and Removal](https://medium.com/analytics-vidhya/removing-outliers-understanding-how-and-what-behind-the-magic-18a78ab480ff) This is done in Python but the concepts are the same and we can easily do these in Ruby Polars. Introduces you to IQR and Standard Deviation, the two main outlier removal types.
```Ruby
# Std Deviation
quantity_outliers = df.filter(
    (Polars.col('selected_column') < (Polars.col('selected_column').mean() - (3 * Polars.col('selected_column').std())))
    | (Polars.col('selected_column') > (Polars.col('selected_column').mean() + (3 * Polars.col('selected_column').std())))
)

#IQR
s = Polars::Series.new("Measurements", [-1.01,  0.86, -4.60, 3.98,  0.53, -7.04, 3.98,  0.53, -7.04])
s.quantile(0.75, interpolation:"nearest")
```
