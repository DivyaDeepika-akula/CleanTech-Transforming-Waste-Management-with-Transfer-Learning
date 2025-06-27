project executable file
here is the code :
import time
import os
import random
CLASS_NAMES = ['cardboard', 'glass', 'metal', 'paper', 'plastic', 'trash']
def load_waste_classification_model(model_path="waste_classifier.h5"):
    print(f"Initializing model from '{model_path}'...")
    print("This would typically take a few moments.")
    time.sleep(2)
    mock_model = "SimulatedWasteClassifier_v1.0"
    print("--- Mock Model Loaded Successfully ---")
    return mock_model
def classify_waste_item(model, image_path):

    print(f"\n-> Analyzing item from image: '{os.path.basename(image_path)}'")
    time.sleep(0.5)
    filename = os.path.basename(image_path).lower()
    for class_name in CLASS_NAMES:
        if class_name in filename:
            print(f"   Model Prediction: {class_name.capitalize()}")
            return class_name

    # If no class is found in the filename, classify as 'trash'
    print("   Model Prediction: Unclassified, defaulting to Trash")
    return "trash"


def activate_sorting_mechanism(waste_type):
    """
    Simulates activating the correct physical sorter based on classification.
    """
    print(f"   Classification Confirmed: {waste_type.upper()}")

    if waste_type == 'plastic':
        print("   ACTION: Firing pneumatic air jet to push item into [PLASTIC BIN].")
    elif waste_type == 'metal':
        print("   ACTION: Engaging overhead electromagnet to lift item into [METAL BIN].")
    elif waste_type == 'glass':
        print("   ACTION: Tilting conveyor section to slide item into [GLASS BIN].")
    elif waste_type == 'paper' or waste_type == 'cardboard':
        print(f"   ACTION: Firing pneumatic air jet to push item into [PAPER/CARDBOARD BIN].")
    elif waste_type == 'trash':
        print("   ACTION: No action taken. Item proceeds to [LANDFILL/INCINERATOR BIN].")
    else:
        print(f"   WARNING: Unknown waste type '{waste_type}'. Defaulting to [LANDFILL BIN].")
    print("--- Action Complete ---")
if __name__ == "__main__":
    print("==============================================")
    print("=== Automated Waste Sorting System STARTUP ===")
    print("==============================================\n")
    sorter_model = load_waste_classification_model()
    sample_items = [
        "images/item_001_plastic_bottle.jpg",
        "images/item_002_soda_can_metal.jpg",
        "images/item_003_apple_core_trash.jpg", # Organic waste is often 'trash' in simple models
        "images/item_004_newspaper_paper.jpg",
        "images/item_005_beer_bottle_glass.png",
        "images/item_006_amazon_box_cardboard.jpg",
        "images/item_007_crushed_tin_foil_metal.tiff",
        "images/item_008_styrofoam_cup_trash.bmp",
    ]

    print("\nConveyor belt starting... Simulating item detection.\n")
    time.sleep(2)
 # Process each item in the sample list
    for item_image in sample_items:
        predicted_type = classify_waste_item(sorter_model, item_image)
        activate_sorting_mechanism(predicted_type)
        time.sleep(3)

    print("\n============================================")
    print("=== All items processed. System shutting down. ===")
    print("============================================")
