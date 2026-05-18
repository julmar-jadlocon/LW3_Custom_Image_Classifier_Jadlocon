# LW3_Custom_Image_Classifier_Jadlocon

Colab link - https://colab.research.google.com/drive/1ljm7MkA4Vls8PQU-N4Z5Jb_Kaq_zYt6q?usp=sharing


GUIDE QUESTION

1. Dataset Preparation
In Google Drive, you organized the dataset by creating a main folder containing subfolders for each category 
(or "class") of images. This specific folder structure is vital because TensorFlow's image_dataset_from_directory 
function uses those subfolder names to automatically label your data. If all the images were in one giant folder, 
the computer wouldn't know which image belongs to which category.

2. Model Training
Convolutional layers act like filters that scan your images to find patterns. Early layers might find simple edges
or colors, while deeper layers recognize complex shapes like eyes or wheels. We split the data into training and 
validation sets to ensure the model isn't just "cheating" by memorizing. The training set is for learning, and the 
validation set is a "practice test" with new images to see if the model actually understands what it’s looking at.

3. Performance Analysis
Your model achieved a very high training accuracy (about 98%), but a much lower validation accuracy (about 28%). 
This gap suggests that the number of images might have been too small for the complexity of the model, leading it 
to overfit. Generally, more images help the model see more variations of an object, which improves its ability to 
recognize that object in the real world.

4. Critical Thinking
One major challenge was encountering "overfitting," where the model got too specific to the training photos and 
failed on new ones. Another challenge was managing file paths and ensuring Google Drive stayed connected. Data 
augmentation helps solve this by creating "fake" new data—flipping, rotating, or zooming into existing images—so 
the model has to learn the core features of an object rather than just its exact position in a photo.

5. Application
A real-world application for this model could be an automated sorting system, such as an app that identifies plant 
diseases from a leaf photo or a tool that sorts recyclable materials. To integrate this into a mobile or web app,
you would save the trained model (often as a TFLite file for mobile) and use a framework like TensorFlow.js (for web) 
or Flutter (for mobile) to allow users to upload photos and get instant predictions.

GUIDE QUESION 2

Visualization & Overfitting
1. Signs of Overfitting: In the first model, the clearest sign of overfitting was a massive "gap" between the training
accuracy and the validation accuracy. The training accuracy climbed to nearly 98%, while the validation accuracy stayed 
stuck around 28%. On the graph, this looked like the two lines were moving away from each other—the training line kept 
going up, while the validation line stayed flat or even dropped.

2. Effect of Data Augmentation: Data augmentation made the training process "harder" for the model. It caused the training 
accuracy to drop from that fake 98% down to a more honest 38%, but it helped the validation accuracy stay much closer to 
the training score. It essentially "closed the gap," ensuring the model was actually learning features rather than just 
memorizing the training set.

Model Improvement
3. Purpose of Dropout Layers: Dropout layers act like a "strength training" exercise for the neural network. By randomly 
"turning off" a percentage of neurons during training, the model is forced to find multiple ways to recognize an object. 
It prevents the model from becoming overly dependent on a few specific pixels or patterns, which makes the overall "brain" 
of the AI more robust and flexible.

4. Why Augmentation Improves Generalization: Generalization is the model's ability to recognize an object it hasn't seen
before. Data augmentation improves this by creating variations of your existing images—flipping them, rotating them, or
zooming in. This teaches the model that a "Marigold" is still a "Marigold" even if it's upside down or off-center, which 
helps the model perform better in the unpredictable real world.

Performance Comparison
5. Accuracy Comparison: Before the improvements, the model was "lying" with a 98% training accuracy that failed on new 
data. After the improvements, the accuracy reached about 38% for training and 33% for validation. While the number is 
lower, the model is significantly better because it is now "honest"—its performance on new images is almost as good as 
its performance on the ones it studied.

6. Most Impactful Technique: Data Augmentation likely contributed the most to the improvement. While Dropout helps with
the internal logic, Data Augmentation fundamentally changed how the model saw the data, preventing it from ever seeing
the exact same image twice and forcing it to learn the actual shapes and colors of the flowers.

Deployment & Application
7. Importance of Saving: Saving the model is crucial because it "freezes" the trained weights and architecture into a 
file (like your .keras file). Without saving, all the progress the model made during training would be lost the moment 
you close your Google Colab session. Saving allows you to skip the long training process and jump straight to making 
predictions later.

8. Real-World Deployment: This system can be deployed by taking the saved file and putting it into a mobile app or a 
website. For example, a gardener could take a photo of a flower with their phone, and the app would send that image 
to the "saved brain" to identify the species instantly. This is how apps like "PlantSnap" or "Google Lens" work in daily 
life.
