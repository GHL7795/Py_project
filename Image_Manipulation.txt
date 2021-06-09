from PIL import Image, ImageEnhance, ImageOps, ImageFilter

DEFAULT_FILE = 'flower.jpg'

def get_file():
    filename = input('Enter image file (or press enter for default): ')
    if filename == '':
        filename = DEFAULT_FILE
    return filename

def imageformat(filename):
    img = Image.open(filename)
    return img.format

def imagemode(filename):
    img = Image.open(filename)
    return img.mode

def imagesize(filename):
    img = Image.open(filename)
    return img.size

def imageresize(filename):
    img = Image.open(filename)
    width = int(input("enter new width\n>> "))
    height = int(input("enter new height\n>> "))
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    small_img = img.resize((width,height))
    small_img.save(rename)

def imagethumbnail(filename):
    img = Image.open(filename)
    width = int(input("enter new width\n>> "))
    height = int(input("enter new height\n>> "))
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    small_img = img.thumbnail((width,height))
    small_img = img.save(rename)

def imagecrop(filename):
    img = Image.open(filename)
    x_coordinate = int(input("enter x coordinate for cropping\n>> "))
    y_coordinate = int(input("enter y coordinate for cropping\n>> "))
    width = int(input("enter new pixel width\n>> "))
    height = int(input("enter new pixel height\n>> "))
    cropped_img = img.crop((x_coordinate,y_coordinate,width,height))
    rename = input("enter the name of new image{eg:image_name.jpg}nif you want to save in a new location , enter the image path\n>> ")
    cropped_img.save(rename)

def imagerotate(filename):
    img = Image.open(filename)
    angle = int(input("enter angle of rotation\n>> "))
    img9 = img.rotate(angle)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    img9.save(rename)

def imageflip(filename):
    img = Image.open(filename)
    while True :
        ad = int(input("enter 1 to flip the image from left to right\nenter 2 to flip the image from top to bottom\n>>"))
        if ad == 1 or ad == 2 :
            break
        else:
            print("enter valid choice")
            continue
    if ad == 1 :
        img_flipLR = img.transpose(Image.FLIP_LEFT_RIGHT)
        rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
        img_flipLR.save(rename)
    else:
        img_flipTB = img.transpose(Image.FLIP_TOP_BOTTOM)
        rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
        img_flipTB.save(rename)

def imagegrayscale(filename):
    img = Image.open(filename)
    grey_img = img.convert("L")
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    grey_img.save(rename)

def imagergb(filename):
    img = Image.open(filename)
    rgb_img = img.convert("RGB")
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    rgb_img.save(rename)

def imagecmyk(filename):
    img = Image.open(filename)
    cmyk_img = img.convert("CMYK")
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    cmyk_img.save(rename)

def imageextension(filename):
    img = Image.open(filename)
    rename = input("enter the name of new image{eg:image_name.jpg}\n1.image_name.jpg for jpeg extension\n2.image_name.png for png extension\n3.image_name.pdf for pdf extension\nif you want save in a new location , enter the image path\n>> ")
    img.save(rename)

def imagesharpness(filename):
    img = Image.open(filename)
    ad = float(input(">enter the values between 0.0 - 0.9 to decrease the sharpness of the image\n>enter 1.0 to retain the same image without any changes\n>enter the values above 1.1 to increase the sharpness of the image\n>>"))
    enhancer = ImageEnhance.Sharpness(img)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path ")
    enhancer.enhance(ad).save(rename)

def imagecolor(filename):
    img = Image.open(filename)
    ad = float(input(">enter the values between 0.0 - 0.9 to decrease the color of the image\n>enter 1.0 to retain the same image without any changes\n>enter the values above 1.1 to increase the color of the image\n>>"))
    enhancer = ImageEnhance.Color(img)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    enhancer.enhance(ad).save(rename)

def imagebrightness(filename):
    img = Image.open(filename)
    ad = float(input(">enter the values between 0.0 - 0.9 to decrease the brightness of the image\n>enter 1.0 to retain the same image without any changes\n>enter the values above 1.1 to increase the brightness of the image\n>>"))
    enhancer = ImageEnhance.Brightness(img)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    enhancer.enhance(ad).save(rename)

def imagecontrast(filename):
    img = Image.open(filename)
    ad = float(input(">enter the values between 0.0 - 0.9 to decrease the contrast of the image\n>enter 1.0 to retain the same image without any changes\n>enter the values above 1.1 to increase the contrast of the image\n>>"))
    enhancer = ImageEnhance.Contrast(img)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    enhancer.enhance(ad).save(rename)

def imageinvert(filename):
    img = Image.open(filename)
    inverted = ImageOps.invert(img)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    inverted.save(rename)

def imagegaussianblur(filename):
    img = Image.open(filename)
    ad = float(input(">enter 0.0 to retain the same image without any changes\n>enter the values above 0.0 to increase the amount of blur\n>>"))
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    img.filter(ImageFilter.GaussianBlur(ad)).save(rename)

def imagedetail(filename):
    img = Image.open(filename)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    img.filter(ImageFilter.DETAIL).save(rename)

def imagesmooth(filename):
    img = Image.open(filename)
    rename = input("enter the name of new image{eg:image_name.jpg}\nif you want to save in a new location , enter the image path\n>> ")
    img.filter(ImageFilter.SMOOTH).save(rename)
    
def question():
    print("Wanna try it again ?")
    while True:
        ques=int(input(">enter 1 for YES\n>enter 0 for NO\n>>"))
        if ques == 1 or ques == 0:
            return ques
            break
        else:
            pass

def main():
    while True:
        filename = get_file()
        task_list = ["image_format","image_mode","image_size","image_resize","image_thumbnail","image_crop","image_rotate","image_flip","image_grayscale","image_rgb","image_cmyk","image_extension","image_sharpness","image_color","image_brightness","image_contrast","image_invert","image_gaussianblur","image_detail","image_smooth"]
        print("1.image_format\n2.image_mode\n3.image_size\n4.image_resize\n5.image_thumbnail\n6.image_crop\n7.image_rotate\n8.image_flip\n9.image_grayscale\n10.image_rgb\n11.image_cmyk\n12.image_extension\n13.image_sharpness\n14.image_color\n15.image_brightness\n16.image_contrast\n17.image_invert\n18.image_gaussianblur\n19.image_detail\n20.image_smooth")
        task=input("enter the task to be done in the given list of tasks ")
        if task in task_list :
            pass
        else:
            print("enter the task name as it is in the list")
            continue
        if task == "image_format":
            pic1=imageformat(filename)
            print(pic1)
        elif task == "image_mode":
            pic2=imagemode(filename)
            print(pic2)
        elif task == "image_size":
            pic3=imagesize(filename)
            print(pic3,"note:size in width,height")
        elif task == "image_resize":
            imageresize(filename)
        elif task == "image_thumbnail":
            imagethumbnail(filename)
        elif task == "image_crop":
            imagecrop(filename)
        elif task == "image_rotate":
            imagerotate(filename)
        elif task == "image_flip":
            imageflip(filename)
        elif task == "image_grayscale":
            imagegrayscale(filename)
        elif task == "image_rgb":
            imagergb(filename)
        elif task == "image_cmyk":
            imagecmyk(filename)
        elif task == "image_extension":
            imageextension(filename)
        elif task == "image_sharpness":
            imagesharpness(filename)
        elif task == "image_color":
            imagecolor(filename)
        elif task == "image_brightness":
            imagebrightness(filename)
        elif task == "image_contrast":
            imagecontrast(filename)
        elif task == "image_invert":
            imageinvert(filename)
        elif task == "image_gaussianblur":
            imagegaussianblur(filename)
        elif task == "image_detail":
            imagedetail(filename)
        elif task == "image_smooth":
            imagesmooth(filename)
        hint=question()
        if hint == 1:
            pass
        elif hint == 0:
            break
        


    
if __name__ == '__main__':
    main()
