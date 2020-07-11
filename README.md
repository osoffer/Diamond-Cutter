# Diamond Cutter 
A tool that uses the power of explainability and interpretability, for the process of choosing a CNN model for transfer learning.

The tool visualizes the top channel activations for transferred models that were trained to classify new data. 
<br>Diamond Cutter allows a bulk process of “cutting” multiple models, in multiple layer positions, and training them for the purpose of classifying new data. 
<br>It will feature all mainstream CNN models used for transfer learning.
<br>The project combines & alters existing projects in the fields explainability & interpretability, for these specific purpose.

<i>\* The project is not yet completed, view it’s progress at the bottom of the page.</i>

## Visualization tools
<br><b>Channel Attribution</b> – shows what are the top activated channels for specific image/s.<br>This tool allows a better understanding of what patterns & textures the model focuses on when classifying your data.
<br>
<br>
<img src="https://raw.githubusercontent.com/osoffer/Diamond-Cutter/master/images/Channel%20Attribution%20-%20Dylia6.png" width=800px>
<br>
<br>
<br><b>Semantic Map</b> – splits an image to spatial cells and shows top activated channels for each cell.<br>This tool allows a better understanding of what area of the image the model focuses on when classifying your data.
<br>
<br>
<img src="https://raw.githubusercontent.com/osoffer/Diamond-Cutter/master/images/Activation Maps - Dylia.png" width=700px>
<br>
<br>
## Credit
Diamond Cutter is based on the following tools & research: 
<br><b>Lucid Framework</b> https://github.com/tensorflow/lucid
<br><b>Feature Visualization</b> - How neural networks build up their understanding of images, https://distill.pub/2017/feature-visualization/
<br><b>The Building Blocks of Interpretability</b> - https://distill.pub/2018/building-blocks/
<br>
<br><i>Related work, not included in this project:
<br><b>Zoom In: An Introduction to Circuits</b> - https://distill.pub/2020/circuits/zoom-in/
<br><b>Exploring Neural Networks with Activation Atlases</b> - https://distill.pub/2019/activation-atlas/ </i>

<br>
<br>
<br>
## Features
<br><b>Choosing the right model (& right layer) for Transfer Learning</b>
<br><b>1. Which Model & Layer will Classify My Data With The Highest Accuracy?</b>
<br>&nbsp;&nbsp;&nbsp;- Upload your data
<br>&nbsp;&nbsp;&nbsp;- Choose model/s from the list (inception_v4, nasnet_large, etc.)
<br>&nbsp;&nbsp;&nbsp;- Where to cut: choose specific layer/s from these model/s to add a new output layer to, trained by your data.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example:
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>inception_v4: layer “n” (last before softmax)</i>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>nasnet_large layer “n-1”</i>
<br>&nbsp;&nbsp;&nbsp;- Choose parameters for the training process
<br>&nbsp;&nbsp;&nbsp;- Run training for new output layer/s
<br>&nbsp;&nbsp;&nbsp;- View accuracy values for each layer
<br>
<br>
<b>2. View a generated visualization (so cool!) of the top activated channels in one of the new networks you’ve built in stage 1.</b>
<br>This way you can examine if your data activates channels with relevant patterns.
<br>&nbsp;&nbsp;&nbsp;- Pick a layer of your transferred model
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the layer is in the “frozen” part of the transferred model, visualizations were already generated
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the picked layer is the new output layer, visualizations need to be generated from scratch
<br>
<br><b>Making sure the model (& layer) focuses on a correct object & pattern</b>
<br><b>3. View a generated visualization of the top activated channels per area in image</b>
<br>View a visualization of your data's top activated channels for each area of the image.
This way you can examine if the channel focuses on a correct pattern by image area.
<br>&nbsp;&nbsp;&nbsp;- Pick a layer of your transferred model
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the layer is in the “frozen” part of the transferred model, visualizations were already generated
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- If the picked layer is the new output layer, visualizations need to be generated from scratch
<br>
<br>
<br>
<b>To do list:</b>
<br>Inventory
<br>- Download all the prepared (frozen) models for transfer learning
<br>- Convert models to .modelzoo format
<br>- Upload mozelzoo files to google drive
<br>- Map all relevant layers per model
<br>
<br>Model Training
<br>- Add a general flow for adding a new output layer to a certain layer for a certain model
<br>- Allow persistency, saving new trained models & results to the user’s google drive
<br>- Build a flow for visualization map assembly from generated visualizations
<br>- Generate visualizations for top activated channels for trained model
<br>- Connect visualization maps to Channel Attribution & Semantic Map tools
<br>
<br>User interaction
<br>- Add simple way for the user to view all available models
<br>- Add simple way for the user to choose specific model/s & layer/s to train
<br>- Add simple way for the user to upload data / download from external source
<br>- Add a simple way for the user to map it’s google drive to the notebook for persistency
<br>- Add simple way for the user to pick visualizations for layers
<br>
<br>Visualization – Channel Attribution
<br>- Prepare a general visualization flow for a frozen model
   <br>- Generate all visualizations for prepared models (across all layers and channels)
<br>- Add an option to use visualization flow for a trained model
<br>
<br>Visualization – Semantic Map
<br>- Prepare a general visualization flow for a frozen model
<br>- Add an option to use visualization flow for a trained model
