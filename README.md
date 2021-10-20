# multi_image_picker

Select Multiple images in Flutter...


Add dependecy of image_picker:
       
           image_picker: ^0.8.4+3


 Then make a method for selectImages():

          final ImagePicker imagePicker = ImagePicker();
          List<XFile>? imageFileList = [];

          void selectImages() async {
             final List<XFile>? selectedImages = await 
                    imagePicker.pickMultiImage();
               if (selectedImages!.isNotEmpty) {
                  imageFileList!.addAll(selectedImages);
               }
              print("Image List Length:" + imageFileList!.length.toString());
              setState((){});
          }

Create a builder for showing selected Images:


         return Scaffold(
              appBar: AppBar(
              title: Text('Multiple Images'),
             ),
            body: SafeArea(
               child: Column(
                 children: [
                     ElevatedButton(
                        onPressed: () {
                          selectImages();
                      },
                     child: Text('Select Images'),
                   ),
                   Expanded(
                      child: Padding(
                      padding: const EdgeInsets.all(8.0),
                      child: GridView.builder(
                            itemCount: imageFileList!.length,
                           gridDelegate: 
                              SliverGridDelegateWithFixedCrossAxisCount(
                                  crossAxisCount: 3),
                              itemBuilder: (BuildContext context, int index) {
                               return Image.file(File(imageFileList![index].path), 
                            fit: BoxFit.cover,);
                         }),
                     ),
                   ),
                 ],
                ),
              ));


Complete source code available above in repository.......
