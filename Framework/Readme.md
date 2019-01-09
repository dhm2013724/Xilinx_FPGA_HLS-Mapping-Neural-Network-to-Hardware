#Generate the weight and bias that we need  
(1)You should follow the code in the 'Generate_weight&bias_combine with BN.txt', modify the function load_convolutional_weights in Prase.c, and re-compile the Darknet.  
(2)run ./darknet detect cfg/yolov2.cfg yolov2.weights dog.jpg to generate the weight and bias file.
(3)You will see two files named 'weights.bin' and 'bias.bin', which are used in the next step;
