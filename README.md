pip install ibm-watson
from ibm_watson import VisualRecognitionV3
from ibm_watson.visual_recognition_v3 import Feature

# Replace 'YOUR_API_KEY' with your actual API key
api_key = 'YOUR_API_KEY'
version = '2021-09-27'  # Use the latest version available

# Initialize Visual Recognition service
visual_recognition = VisualRecognitionV3(
    version=version,
    iam_apikey=api_key
)

# Define the image file you want to analyze
with open('<path_to_your_image>', 'rb') as image_file:
    classes = visual_recognition.classify(
        images_file=image_file,
        threshold='0.6',  # Adjust the threshold as needed
        classifier_ids=['default'],  # Use a custom classifier if you've trained one
    ).get_result()

print(classes)
