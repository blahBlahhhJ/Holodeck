## Installation
After cloning the repo, you can install the required dependencies using the following commands:
```
conda create --name holodeck python=3.10
conda activate holodeck
pip install -r requirements.txt
pip install --extra-index-url https://ai2thor-pypi.allenai.org ai2thor==0+8524eadda94df0ab2dbb2ef5a577e4d37c712897
```

## Data
Download the data by running the following commands:
```bash
python -m objathor.dataset.download_holodeck_base_data --version 2023_09_23
python -m objathor.dataset.download_assets --version 2023_09_23
python -m objathor.dataset.download_annotations --version 2023_09_23
python -m objathor.dataset.download_features --version 2023_09_23
```
by default these will save to `~/.objathor-assets/...`, you can change this director by specifying the `--path` argument.  If you change the `--path`, you'll need to set the `OBJAVERSE_ASSETS_DIR` environment variable to the path where the assets are stored when you use Holodeck.

## Usage
You can use the following command to generate a new environment.
```
python holodeck/main.py --query "a living room" --openai_api_key <OPENAI_API_KEY>
```

## Load the scene in Unity
1. Install [Unity](https://unity.com/download) and select the editor version `2020.3.25f1`.
2. Clone [AI2-THOR repository](https://github.com/allenai/ai2thor) and switch to the appropriate AI2-THOR commit.
```
git clone https://github.com/allenai/ai2thor.git
git checkout 07445be8e91ddeb5de2915c90935c4aef27a241d
```
3. Reinstall some packages:
```
pip uninstall Werkzeug
pip uninstall Flask
pip install Werkzeug==2.0.1
pip install Flask==2.0.1
```
3. Load `ai2thor/unity` as project in Unity and open `ai2thor/unity/Assets/Scenes/Procedural/Procedural.unity`.
4. In the terminal, run [this python script](connect_to_unity.py):
```
python connect_to_unity --scene <SCENE_JSON_FILE_PATH>
```
5. Press the play button (the triangle) in Unity to view the scene.
