# tf_cnnvis

tf_cnnvis is an implementation of the paper [Visualizing and Understanding Convolutional Networks](https://www.cs.nyu.edu/~fergus/papers/zeilerECCV2014.pdf) by Matthew D. Zeiler and Rob Fergus. In implementation we uses [TensorFlow](https://www.tensorflow.org/) library to generate reconstruction images from Convolutional Networks.

# Documentation
### get_visualization(graph_or_path, value_feed_dict, input_tensor=None, layers='r', path_logdir='./Log', path_outdir='./Output', force=False, n=8) 
cnnvis main api function
#### Parameters
* graph_or_path (tf.Graph object or String) – TF graph or [Path-to-saved-graph] as String
* value_feed_dict (dict or list) – Values of placeholders to feed while evaluting
    * dict : {placeholder1 : value1, ...}
    * list : [value1, value2, ...]
* input_tensor (tf.tensor object (Default = None)) – tf.tensor object which is an input to TF graph
* layers (list or String (Default = 'r')) – 
    * ‘r’ : Reconstruction from all the relu layers 
    * ‘p’ : Reconstruction from all the pooling layers 
    * ‘c’ : Reconstruction from all the convolutional layers
* path_outdir (String (Default = "./Output")) – [path-to-dir] to save results into disk as images
* path_logdir (String (Default = "./Log")) – [path-to-log-dir] to make log file for TensorBoard visualization
* force (boolean (Default = False)) – True to took of limit for number of featuremaps in a layer
* n (int (Default = 8)) – Number of gradient ops will be added to the graph to avoid redundent forward pass

#### Return
* is_success (boolean) – True if not errors. False otherwise

### image_normalization(image, ubound=255.0, epsilon=1e-07)
Min-Max image normalization. Convert pixle values in range [0, ubound]
#### Parameters
* image (3-D numpy array) – A numpy array to normalize
* ubound (float (Default = 255.0)) – upperbound for a image pixel value
* epsilon (float (Default = 1e-7)) – for computational stability

#### Return
* (3-D numpy array) – A normalized image

### convert_into_grid(Xs, ubound=255.0, padding=1)
Convert 4-D numpy array into a grid image
#### Parameters
* Xs (4-D numpy array (first axis contations an image)) – A numpy array of images to make grid out of it
* ubound (float (Default = 255.0)) – upperbound for a image pixel value
* padding (int (Default = 1)) – padding size between grid cells

#### Return
* (3-D numpy array) – A grid of input images
