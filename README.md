# Diamond Cutter 
A tool that uses the power of explainability and interpretability, for the process of choosing a CNN model for transfer learning.

The tool visualizes the top channel activations for state-of-the-art CNN models, in different layouts. 
<br>Diamond Cutter will allow a bulk process of “cutting” multiple models, in multiple layer positions, and training them for the purpose of classifying new data and analyzing results by visualizations. 
<br>It will feature all mainstream CNN models used for transfer learning.
<br>The project combines & alters existing projects in the fields explainability & interpretability.

Notes:
<br><i>\* This tool is not yet completed, view it’s progress at the bottom of the page.</i>
<br><i>\* Project's code is a mesh of code from multiple projects.</i>

## Visualization tools
<b>Channel Attribution</b> – shows visualizations of the top activated channels for specific image/s.<br>This tool allows a better understanding of what patterns & textures the model focuses on when classifying your data.
<br>
<br>
<img src="https://raw.githubusercontent.com/osoffer/Diamond-Cutter/master/images/Channel%20Attribution%20-%20Dylia6.png" width=800px>
<br>
<br>
<br><b>Semantic Map, Heatmap</b> – splits an image to spatial cells and shows top activated channels for each cell.<br>This tool allows a better understanding of what area of the image the model focuses on when classifying your data.
<br>
<br>
<img src="https://raw.githubusercontent.com/osoffer/Diamond-Cutter/master/images/Activation Maps - Dylia.png" width=700px>
<br>
<br>
## Acknowledgments
Diamond Cutter is based on the following tools & research: 
<br><b>Lucid Framework</b> https://github.com/tensorflow/lucid
<br><b>Feature Visualization</b> https://distill.pub/2017/feature-visualization/
<br><b>The Building Blocks of Interpretability</b> https://distill.pub/2018/building-blocks/
<br>
<br><i>Related work, not included in this project:
<br><b>Zoom In: An Introduction to Circuits</b> https://distill.pub/2020/circuits/zoom-in/
<br><b>Exploring Neural Networks with Activation Atlases</b> https://distill.pub/2019/activation-atlas/ </i>
<br>
<br>
## Features
<b>1. View a visualization (so cool!) of top activated channels in a CNN models for transfer learning (and modified networks in the future) with your data.</b>
<br>This way you're able to examine if your data activates channels with relevant patterns.
<br><b>Note:</b> This feature is not yet completed, you can only visualize channels from original "frozen" models.
          <br><i>Available models: inception_v1, inception_v4.</i>
<br>&nbsp;&nbsp;&nbsp;- Pick a layer of your transferred model
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the layer is in the “frozen” part of the transferred model, visualizations were already generated
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the picked layer is the new output layer, visualizations need to be generated from scratch
<br>
<br><b>Making sure the model (& layer) focuses on a correct object & pattern</b>
<br><b>2. View a generated visualization of the top activated channels per area in image</b>
<br>View a visualization of your data's top activated channels for each area of the image.
This way you can examine if the channel focuses on a correct pattern by image area.
<br>Negative example: focusing on a reflection coming from a product's label instead of label's content.
<br><b>Note:</b> This feature is not yet completed, you can only visualize channels from original "frozen" models.
          <br><i>Available models: inception_v1, inception_v4.</i>
<br>&nbsp;&nbsp;&nbsp;- Pick a layer of your transferred model
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the layer is in the “frozen” part of the transferred model, visualizations were already generated
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the picked layer is the new output layer, visualizations need to be generated from scratch
<br>
<br>4. View a heatmap of channel activations for your specified class.
<br>This way you can examine if the model focuses on the correct area in your image for its classification.
<br>Negative example: focusing on dog food when predicting "dog".
<br>
<br><b>(FUTURE) Choosing the right model (& right layer) for Transfer Learning</b>
<br><b>4. Which model & layer classifies my data the best?</b>
<br><b>Note:</b> This feature is not yet completed, you can only choose specific model & layer combinations, and classify to existing imagenet classes.
<br>&nbsp;&nbsp;&nbsp;- Upload your data
<br>&nbsp;&nbsp;&nbsp;- Choose model/s from the list (inception_v4, nasnet_large, etc.)
<br>&nbsp;&nbsp;&nbsp;- Where to cut: choose specific layer/s from these model/s to add a new output layer to, trained by your data.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example:
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>inception_v4: layer “n” (last before output)</i>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>nasnet_large layer “n-1”</i>
<br>&nbsp;&nbsp;&nbsp;- Choose parameters for the training process
<br>&nbsp;&nbsp;&nbsp;- Run training for new output layer/s
<br>&nbsp;&nbsp;&nbsp;- View & compare classifications for each model-layer combo
<br>
✔️<b> To do list </b>✔️<br>
<br><b>Model Inventory</b>
<br>- Test all prepared models from lucid’s inventory
<br>&nbsp;&nbsp;&nbsp;- model list: ✔️ InceptionV1, InceptionV2, InceptionV3, ✔️ InceptionV4, NasnetLarge, NasnetMobile, PnasnetLarge, PnasnetMobile, VGG16, VGG19, ResnetV1_50, ResnetV1_101, ResnetV1_152, InceptionResnetV2, MobilenetV1_025, MobilenetV1_050, AlexNet
<br>&nbsp;&nbsp;&nbsp;- if model doesn’t exist, convert model to modelzoo format & import to project
<br>- For each model, map the following artifacts: output layer name, output layer size, pre-output layer name, desired image shape, layer names coupled with square root of layer size (for “spritemap”), layer list - sorted by position in network (ascending)
<br>
<br><b>Visualizations - General</b>
<br>- ✔️ Generalize channel visualization generation flow for all “frozen” models (original tool includes visualization only for Inception V4)
<br>- ✔️ Build a “spritemap” assembly script – the visualization tools extract layer’s channel visualizations from a large image that maps all of them, ordered by channel index
<br>- Generate visualizations for each layer of each model. 
<br>&nbsp;&nbsp;&nbsp;This takes a lot of time in Google colab terms. 
<br>&nbsp;&nbsp;&nbsp;Inception V1 was a small network compared to Inception V4 and Nasnet Large for example (more layers per model, more channels per layer). 
<br>- Channel visualizations are made by a process similar to adversarial networks, to prevent reaching to an adversarial “level”, various regularization techniques are used. Original regularization parameters worked well on Inception V1, for more models further parameter optimization is needed, visualizations look vague.
<br>- Build channel visualization generation flow for new layers that are attached to the original “frozen” model layers
<br>
<br><b>Model Training</b>
<br>- Add a general flow for attaching a new output / convolution layer to a certain layer for a certain model
<br>- Build a comparison flow between for transferred model prediction values
<br>- Allow persistency, saving new trained models & results to the user’s google drive
<br>
<br><b>User Interface</b> 
<br>- Add simple way for the user to view all available models
<br>- Add simple way for the user to view all layers in model
<br>- Add simple way for the user to attach new output / convolution layers to a “frozen” model, “cutting at a certain layer
<br>- Add a plot comparing model prediction rates
<br>- Add simple way for the user to upload data / download from external source
<br>- Add a simple way for the user to map it’s google drive to the notebook for persistency
<br>- Notify user about expected image size for each model

<br><b>Visualization – Channel Attribution</b>
<br>- ✔️ Generalize tool’s flow for compatibility compatibility to all models
<br>- ✔️ Original tool compares 2 classes as positive & negative:  build an option for only 1 class (without negative class)
<br>- ✔️ Build an option to include multiple images, and get their overall top activated channels
<br>- Build an option for an automatic pick for the channels of the class with the highest prediction value (positive class)
<br>- Build an option for an automatic pick for the channels of the class with the second-highest prediction value (negative class)
<br>- Generate all visualizations for prepared models (across all layers and channels)
<br>- Add an option to use Channel Attribution visualization flow for a new layers added to transferred model
<br>
<br><b>Visualization – Semantic Map, Heatmap</b>
<br>- Combine Semantic Map & Heatmap to a single tool
<br>- ✔️ Generalize Semantic Map & Heatmap visualization flows for all models
<br>- ✔️ Heatmap: original tool presents heatmaps of 2 classes as positive & negative (orange, blue) 
<br>&nbsp;&nbsp;&nbsp;- Add an option for only 1 class (without a negative class)
<br>&nbsp;&nbsp;&nbsp;- Add an option for an automatic pick for the channels of the class with the highest prediction value (positive class)
<br>&nbsp;&nbsp;&nbsp;- Add an option for an automatic pick for the channels of the class with the second-highest prediction value (negative class)
<br>- Add an option to use Semantic Map & Heatmap for a new output / convolutional layers added to “frozen” models
<br>- Semantic Map: Build an option to present top channel activations for a specific class
<br>&nbsp;&nbsp;&nbsp;- Build an option for an automatic pick for the channels of the class with the highest prediction value
