<h1> Retraining Google Coral Neural Networks </h1>

<h2> What is the Google Coral? </h2>

The Google Coral USB Accelerator is an AI hardware accelerator that plugs into the Limelight 3 to run neural networks for custom object detection (game pieces, field elements, etc.).

<h2> When to Retrain Neural Networks </h2>

Retrain when:
- New game requires different object detection
- Existing model not detecting accurately
- Lighting conditions change significantly
- Game piece design changes
- Adding new detection classes
- Improving detection confidence

<h2> Training Process Overview </h2>

The neural network training pipeline:
1. Collect training images
2. Label images with bounding boxes
3. Train model using TensorFlow/PyTorch
4. Convert to Edge TPU format
5. Upload to Limelight
6. Test and iterate

<h2> Collecting Training Data </h2>

**Image Collection Best Practices**:
- **Variety**: Multiple angles, distances, lighting
- **Quantity**: 500-2000+ images per class
- **Conditions**: Match competition environment
- **Backgrounds**: Include field elements
- **Orientations**: Objects in various positions

**Collection Methods**:
- Limelight snapshot feature
- Manual photography
- Video frame extraction
- Team-shared datasets (Chief Delphi)

<h2> Labeling Images </h2>

Use labeling tools like:
- **Roboflow**: Web-based, easy to use
- **CVAT**: Open source, powerful
- **LabelImg**: Desktop application

For each image:
- Draw bounding boxes around objects
- Assign correct class labels
- Verify accuracy
- Export in compatible format (COCO, Pascal VOC)

<h2> Training Models </h2>

**Option 1: Limelight Training Pipeline**:
- Upload labeled dataset to Limelight
- Use Limelight's cloud training service
- Automatic conversion to Edge TPU format
- Simple but less control

**Option 2: Google Colab/Custom Training**:
- Use TensorFlow or PyTorch
- Train on Google Colab (free GPU)
- More control over model architecture
- Requires ML expertise

**Option 3: Roboflow Training**:
- Upload to Roboflow
- Train in cloud
- Export for Edge TPU
- User-friendly interface

<h2> Model Conversion </h2>

To run on Google Coral:
- Model must be TensorFlow Lite format
- Compiled for Edge TPU
- Quantized (INT8)
- Optimized for inference speed

Use Edge TPU Compiler:
```bash
edgetpu_compiler model.tflite
```

<h2> Uploading to Limelight </h2>

**1. Access Limelight Web Interface**:
- Navigate to http://limelight.local:5801/

**2. Go to Neural Network Tab**:
- Select neural network pipeline

**3. Upload Model**:
- Choose compiled .tflite file
- Upload labels file (.txt)
- Configure detection parameters

**4. Configure Pipeline**:
- Set confidence threshold
- Adjust detection regions
- Configure output format

<h2> Testing and Validation </h2>

After uploading model:
- **Test with real objects**: Verify detection
- **Check confidence scores**: Should be >70%
- **Test in various lighting**: Match competition
- **Measure inference time**: Should be <50ms
- **Test at competition distances**: Realistic range
- **Check false positives**: Minimize incorrect detections

<h2> Iteration and Improvement </h2>

If model isn't accurate:
- Collect more training images (especially missed cases)
- Add more variety to training data
- Adjust model architecture
- Fine-tune detection threshold
- Add hard-negative examples (false positives)
- Retrain with augmented data

<h2> Integration with Robot Code </h2>

Access neural network results in code:
```java
// Get neural network detections
LimelightResults results = LimelightHelpers.getLatestResults("limelight");
Detector[] detectors = results.targetingResults.detector_results;

for (Detector detector : detectors) {
    String className = detector.className;
    double confidence = detector.confidence;
    double[] bbox = detector.bbox;  // [x, y, width, height]
}
```

<h2> Best Practices </h2>

- Start training early in build season
- Collect diverse training data
- Test on actual robot/field
- Keep training data organized
- Document model versions and performance
- Have fallback detection methods
- Practice switching between pipelines
- Test in pit and match conditions

<h2> Resources </h2>

- Limelight neural network docs: https://docs.limelightvision.io/
- TensorFlow Lite: https://www.tensorflow.org/lite
- Edge TPU Compiler: https://coral.ai/docs/edgetpu/compiler/
- Roboflow: https://roboflow.com/
- FRC ML resources on Chief Delphi

<h2> Competition Considerations </h2>

- Have multiple trained models ready
- Test models before each match
- Monitor detection confidence
- Have non-neural-network fallback
- Don't rely solely on neural detection
- Document which model is being used
