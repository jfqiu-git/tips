### Extend CNN Memory Usage
	[https://github.com/BVLC/caffe/pull/2016/files]

### Edit *.cpp
   1. [include/caffe/vision_layers.hpp]

       int col_offset_;
       int output_offset_;
       - Blob<Dtype> col_buffer_;
       + static Blob<Dtype> col_buffer_;
       Blob<Dtype> bias_multiplier_;
 

### Edit *.cpp
   2. [src/caffe/layers/base_conv_layer.cpp]

       namespace caffe 
       {
           template <typename Dtype>
           + Blob<Dtype> BaseConvolutionLayer<Dtype>::col_buffer_;
           + template <typename Dtype>
            void BaseConvolutionLayer<Dtype>::LayerSetUp(const vector<Blob<Dtype>*>& bottom,
                 const vector<Blob<Dtype>*>& top) {
          		// Configure the kernel size, padding, stride, and inputs.
