# Histo_Unet
This Code explores semantic segmentation to optimize sparsely annotated histology image analysis for head and neck cancer.

The precise segmentation of cancerous tissues in histology images is critical in medical diagnostics, particularly in the context of head and neck squamous cell carcinoma (HNSCC). This project focuses on tissue segmentation in carcinoma of the tongue slides stained with Hematoxylin and Eosin (H&E) and then digitized for analysis. Our goal was to create an automated system capable of high-quality tumor tissue segmentation, allowing us to export our predictions to QuPath for further analysis by medical professionals. This step is critical in analyzing tumor growth and infiltration patterns, which are important predictors of patient outcome.
The manual annotations available were sparse, posing a significant challenge. As a result, we focused on semantic segmentation on these sparsely annotated images, with a special emphasis on the central tumor as the region of interest (ROI). To address the absence of detailed annotations, we introduced the concept of semi-ground truth—a methodology that recognizes the incomplete and uncertain nature of the available ground truth data, which informed the development and training of our models.
We thoroughly engineered a pipeline that included Python pre-processing techniques like normalization, class refinement and augmentation and Groovy programming language for tile extraction. Our research into Unet variants led us to choose an efficientnetb0 backbone to speed up training. This decision was influenced by pre-training strategies that guided the model toward convergence while optimizing tumor detection in a four- class segmentation problem. The evaluation metrics were selected with care to prioritize intersection over union, reflecting the clinical emphasis on tumor classification.
We used an overlap-tile strategy for predictions during the inference phase, with a 16-fold overlap to ensure comprehensive coverage and diverse perspectives. To refine the final predictions, post-processing methods such as kernel-based smoothing and morphological operations were used. Our findings can be seen in a set of models, each with its own filter sizes, overlapping strategies, and varied use of kernels.

There are 3 folders. 'training' which the model training process happens in it. the 'gif_making' which makes a smaller data set and makes a gif through each epoch of the training. The 'inference' part which would gets whole slides as input and and return the predicted cancer segments into qupath automatically. 
