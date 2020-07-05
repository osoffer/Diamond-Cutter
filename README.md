<big><b>Diamond Cutter</b></big> is a tool that uses the power of explainability and Interpretability, for the process of choosing a CNN model for transfer learning.

The tool visualizes the top channel activations for transferred models that were trained to classify your data. 
<br>Diamond Cutter allows a bulk process of “cutting” multiple models, in multiple layer positions, and training them for the purpose of classifying new data. 
<br>It features all mainstream models used for transfer learning.

Diamond Cutter includes 2 visualization tools:
<br><b>Semantic Map</b> – splits an image to spatial cells and shows top activated channels for each cell.<br>This tool allows a better understanding of what area of the image the model focuses on when classifying your data.
<br><b>Channel Attribution</b> – shows what are the top activated channels for specific image/s.<br>This tool allows a better understanding of what patterns & textures the model focuses on when classifying your data.

<i>\* The project is not yet completed, view it’s progress at the bottom of the page.</i>
<br>
<br>
Diamond Cutter is based on the Lucid Framework https://github.com/tensorflow/lucid,<br>and the following research efforts:
<br><b>Feature Visualization</b> - How neural networks build up their understanding of images, https://distill.pub/2017/feature-visualization/
<br><b>The Building Blocks of Interpretability</b> - https://distill.pub/2018/building-blocks/
<br>Related work, not included in this project:
<br><b>Zoom In: An Introduction to Circuits</b> - https://distill.pub/2020/circuits/zoom-in/
<br><b>Exploring Neural Networks with Activation Atlases</b> - https://distill.pub/2019/activation-atlas/ 

<br>
<br>
The Diamond Cutter produces the following tasks & insights:
<br>Choosing the right model (& right layer) for Transfer Learning
<br>1. Which Model & Layer will Classify My Data With The Highest Accuracy?
<br>- Upload your data
<br>- Choose model/s from the list (inception_v4, nasnet_large, etc.)
<br>- Where to cut: choose specific layer/s from these model/s to add a new output layer to, trained by your data. For example:
<br>   inception_v4: layer “n” (last before softmax), 
<br>   nasnet_large layer “n-1”.
<br>- Choose parameters for the training process
<br>- Run training for new output layer/s
<br>- View accuracy values for each layer

2. View a generated visualization (so cool!) of the top activated channels in one of the new networks you’ve built in stage 1.

This way you can examine if your data activates channels with relevant patterns.
- Pick a layer of your transferred model
   - If the layer is in the “frozen” part of the transferred model, visualizations were already generated
   - If the picked layer is the new output layer, visualizations need to be generated from scratch

Making sure the model (& layer) focuses on a correct object & pattern
3. View a generated visualization of the top activated channels per area in image
View a visualization of your data's top activated channels for each area of the image.
This way you can examine if the channel focuses on a correct pattern by image area.
- Pick a layer of your transferred model
   - If the layer is in the “frozen” part of the transferred model, visualizations were already generated
   - If the picked layer is the new output layer, visualizations need to be generated from scratch

To do list:
Inventory
- Download all the prepared (frozen) models for transfer learning
- Convert models to .modelzoo format
- Upload mozelzoo files to google drive
- Map all relevant layers per model

Model Training
- Add a general flow for adding a new output layer to a certain layer for a certain model
- Allow persistency, saving new trained models & results to the user’s google drive
- Build a flow for visualization map assembly from generated visualizations
- Generate visualizations for top activated channels for trained model
- Connect visualization maps to Channel Attribution & Semantic Map tools

User interaction
- Add simple way for the user to view all available models
- Add simple way for the user to choose specific model/s & layer/s to train
- Add simple way for the user to upload data / download from external source
- Add a simple way for the user to map it’s google drive to the notebook for persistency
- Add simple way for the user to pick visualizations for layers

Visualization – Channel Attribution
- Prepare a general visualization flow for a frozen model
   - Generate all visualizations for prepared models (across all layers and channels)
- Add an option to use visualization flow for a trained model

Visualization – Semantic Map
* based on: _________________
- Prepare a general visualization flow for a frozen model
- Add an option to use visualization flow for a trained model
