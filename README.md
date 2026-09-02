# Fashion-MNIST CNN Classifier

A deep learning web application that classifies clothing images using a **custom-trained CNN** on the Fashion-MNIST dataset. The model was trained in Google Colab and deployed with FastAPI on the backend and a lightweight HTML/CSS/JS frontend, via GitHub + Render.

**Live demo:** https://YOUR-RENDER-URL.onrender.com

> Hosted on Render's free tier — the first request after a period of inactivity may take 30–60 seconds while the service wakes up.

## Features

- Upload a clothing image (JPG, JPEG, PNG, or WEBP, up to 10 MB)
- Get the top-3 predicted classes with confidence scores
- Simple drag-and-drop interface with live image preview
- Health check endpoint for deployment verification

## Model

- **Architecture:** 2 convolutional layers (32 and 64 filters) with max pooling, followed by a dense layer (128 units) with dropout, trained on 28×28 grayscale images
- **Dataset:** Fashion-MNIST (10 clothing classes: T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot)
- **Training:** 10 epochs, Adam optimizer, sparse categorical cross-entropy loss
- **Training notebook:** `training/Fashion_MNIST_CNN_Train_and_Save.ipynb`

> **Note:** This model is trained on 28×28 grayscale Fashion-MNIST images. Real-world photographs of clothing (different lighting, backgrounds, angles) may not classify as reliably as the original dataset's images.

## Tech Stack

- **Backend:** FastAPI, TensorFlow/Keras (custom CNN), Pillow, NumPy
- **Frontend:** HTML, CSS, vanilla JavaScript
- **Deployment:** GitHub + Render

## Project Structure

```
fashion-mnist-classifier/
├── app.py
├── requirements.txt
├── .python-version
├── fashion_cnn_model.keras
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── screenshots/
│   └── prediction-result.png
└── training/
    ├── fashion_cnn_train.py
    └── Fashion_MNIST_CNN_Train_and_Save.ipynb
```

## API Endpoints

| Endpoint       | Method | Description                                      |
|----------------|--------|-----------------------------------------------------|
| `/`            | GET    | Serves the frontend                                |
| `/health`      | GET    | Returns service status                             |
| `/api/predict` | POST   | Accepts an image file, returns top-3 predictions   |

## Running Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Start the server
uvicorn app:app --reload
```

Then open `http://127.0.0.1:8000` in your browser.

## Retraining the Model

1. Open `training/Fashion_MNIST_CNN_Train_and_Save.ipynb` in Google Colab.
2. Run all cells — this trains the CNN and saves `fashion_cnn_model.keras`.
3. Run the final cell to download the model file.
4. Replace the existing `fashion_cnn_model.keras` in the repository root with the new one.

## Deployment

This app is deployed on [Render](https://render.com) as a Python Web Service:

- **Build Command:** `pip install -r requirements.txt`
- **Start Command:** `uvicorn app:app --host 0.0.0.0 --port $PORT`
- **Health Check Path:** `/health`

## Notes

- No API keys or credentials are required to run this app.
- `venv/` and `__pycache__/` are excluded from version control (see `.gitignore`).

-A part of Deep Learning Experiment
