#### Components

Components must support the same operations supported by built-in Unity components without issues, including:

- Enable / disable in runtime.
- Instance / destroy in runtime.
- Instance / destroy prefabs using the component.
- Modify the public properties in the inspector in runtime.
- Modify the public properties from other scripts, both in editor and runtime (use public fields instead of serializable private fields for the properties available in the inspector)
- Hot script reload (use OnEnable/Ondisable instead of Start/Awake/OnDestroy unless it's specifically justified)

## ML Speed Estimator

### Setup
- Go to 'Assets/Features/Speed Estimator/Trainer'
- Create a python environment ```python3 -m venv .venv```
- Activate the virtual environment
- Install the requirements ```pip install -r requirements.txt```
- You can also use ```setup.ps1```

### Train
- Activate your virtual environment
- Run the training script ```python train_speed_estimator.py```
- The input data is 'data/training_data.csv'
- This input data is in the telemetry format
- The output model will be saved in 'model/speed_estimator.onnx'

### Runtime use
- The simulator uses by default the output model of the training process, 'model/speed_estimator.onnx' as runtime model.
- This can be change in the Main Scene. Go to GameObject '424 Nordschleife Scene/PERRINN 424 Nordschleife/SpeedEstimator '. Change 'ModelAsset' in MLSpeedEstimatorContainer component
- MLSpeedEstimatorContainer is the class that uses the trained model to estimate the speed


