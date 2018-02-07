# Custom Vision TensorFlow CLI - Offline image classification using C#
Cross platform CLI to run a pre-trained model exported from CustomVision.ai in the Tensorflow format for image classification using the [TensorFlowSharp library](https://github.com/migueldeicaza/TensorFlowSharp).

To learn more about Microsoft Cognitive Custom Vision Service, please see here: https://azure.microsoft.com/en-gb/services/cognitive-services/custom-vision-service/


## Mean Values (RGB)
Depending on the CustomVision.ai Domain, you'll need to set the appropriate values within the code:

| Project's Domain | Mean Values (RGB) |
|----|----|
|General (Compact) | (123, 117, 104) |
| Landmark (Compact) | (123, 117, 104) |
| Retail (Compact) | (0, 0, 0) |

These are set in BGR eg:

```
// General (Compact) 
// Landmark (Compact)
var bgrValues = new TFTensor(new float[] { 104.0f, 117.0f, 123.0f });
```

```
// Retail (Compact)
var bgrValues = new TFTensor(0f);
```

## CLI Arguments

| Argument name | shortcut | example |
|----|----|----|
| TensorFlowModelFilePath | -m | Assets\model.pb | 
| TensorFlowLabelsFilePath | -l | Assets\labels.txt |
| TestImageFilePath | -t | Assets\test.jpg |

## Usage
- Open the solution
- Restore Nuget Packages
- Run & enjoy

In case you see the following error: 

*Unhandled Exception: System.DllNotFoundException: Unable to load DLL 'libtensorflow': The specified module could not be found.*

Copy the libtensorflow.dll file from the relevant %userprofile%\.nuget\packages\tensorflowsharp runtimes folder of your OS into the same folder as the compiled executable.

### Image classification
The sample TensorFlow model (exported from CustomVision.ai) is for [mushroom classification](https://blogs.msdn.microsoft.com/jamiedalton/2018/01/30/custom-vision-model-for-mushroom-classification-using-bing-images/)
```
CustomVision-TensorFlow.exe -m Assets\model.pb -l Assets\labels.txt -t Assets\test.jpg
```

### Output
Running the above from the command line will display the following:
```
I tensorflow/core/platform/cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
C:\Github\CustomVision-TensorFlow-CSharp\Assets\test.jpg = Agaricus bisporus (92.7477061748505%)
Total time: 00:00:00.4987094
```

### Resources
- Link to [Custom Vision Service Documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/home)
- Link to [Custom Vision with Android](https://github.com/Azure-Samples/cognitive-services-android-customvision-sample)
- Link to [TensorFlow documentation](https://www.tensorflow.org/mobile/)
- Link to [TensorFlowSharp](https://github.com/migueldeicaza/TensorFlowSharp)
- Link to [TensorFlow example code using Python](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/examples/label_image/label_image.py)
- Link to [TensorFlow example code using C++](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/examples/label_image/main.cc)
- Link to [TensorFlow example code using Java](https://github.com/Azure-Samples/cognitive-services-android-customvision-sample/blob/master/app/src/main/java/demo/tensorflow/org/customvision_sample/MSCognitiveServicesClassifier.java)

