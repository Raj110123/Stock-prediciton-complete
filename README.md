
# 📈 Stock Prediction Portal

A full-stack web application for predicting stock prices using deep learning. This project leverages LSTM (Long Short-Term Memory) neural networks to forecast stock market trends and provides an intuitive user interface for visualizing predictions and analysis.

## ✨ Features

- **User Authentication**: Secure JWT-based authentication system with registration and login
- **Stock Data Fetching**: Real-time stock data retrieval using yfinance API
- **Price Visualizations**: Interactive charts displaying:
  - Historical closing prices
  - 100-day moving average (DMA)
  - 200-day moving average (DMA)
- **AI-Powered Predictions**: LSTM neural network model for accurate stock price forecasting
- **Model Evaluation**: Comprehensive metrics including:
  - Mean Squared Error (MSE)
  - Root Mean Squared Error (RMSE)
  - R² Score
- **Responsive Dashboard**: Modern React-based UI for seamless user experience

## 🛠️ Tech Stack

### Backend
- **Framework**: Django 5.0.6
- **API**: Django REST Framework
- **Authentication**: JWT (Simple JWT)
- **Machine Learning**: 
  - TensorFlow/Keras (LSTM Neural Networks)
  - Scikit-learn (MinMaxScaler)
- **Data Processing**: 
  - Pandas
  - NumPy
- **Data Visualization**: Matplotlib
- **Stock Data**: yfinance
- **CORS**: django-cors-headers
- **Configuration**: python-decouple

### Frontend
- **Framework**: React 18.3.1
- **Build Tool**: Vite 5.3.1
- **Routing**: React Router DOM 6.24.1
- **HTTP Client**: Axios 1.7.2
- **Icons**: FontAwesome
- **Styling**: CSS3 with Bootstrap classes

### Database
- **SQLite**: Default Django database for development

## 📁 Project Structure

```
stock-prediction-portal-main/
├── backend-drf/              # Django REST API backend
│   ├── accounts/             # User authentication app
│   ├── api/                  # Stock prediction API
│   ├── stock_prediction_main/ # Django project settings
│   └── stock_prediction_model.keras  # Pre-trained LSTM model
├── frontend-react/           # React frontend application
│   ├── src/
│   │   ├── components/       # React components
│   │   │   ├── dashboard/    # Dashboard component
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   └── ...
│   │   └── ...
│   └── package.json
└── Resources/                # Training data and notebooks
    ├── stock_prediction_using_LSTM.ipynb
    └── stock_prediction_model.keras
```

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Node.js 16+
- npm or yarn

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend-drf
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the `backend-drf` directory:
```
SECRET_KEY=your-secret-key-here
DEBUG=True
```

5. Run migrations:
```bash
python manage.py migrate
```

6. Start the development server:
```bash
python manage.py runserver
```

The backend API will be available at `http://127.0.0.1:8000`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend-react
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the `frontend-react` directory:
```
VITE_BACKEND_ROOT=http://127.0.0.1:8000
```

4. Start the development server:
```bash
npm run dev
```

The frontend will be available at `http://localhost:5173`

## 📊 How It Works

1. **User Registration/Login**: Users create an account and authenticate using JWT tokens
2. **Stock Ticker Input**: Users enter a stock ticker symbol (e.g., AAPL, TSLA, MSFT)
3. **Data Fetching**: The backend fetches 10 years of historical stock data using yfinance
4. **Data Preprocessing**: 
   - Data is split into training (70%) and testing (30%) sets
   - Features are normalized using MinMaxScaler
5. **Prediction**: The pre-trained LSTM model predicts future stock prices
6. **Visualization**: Multiple charts are generated showing:
   - Historical prices
   - Moving averages
   - Predicted vs actual prices
7. **Evaluation**: Model performance metrics are calculated and displayed

## 🧠 Machine Learning Model

The project uses an LSTM (Long Short-Term Memory) neural network architecture:
- **Input Shape**: (100, 1) - 100 days of historical data
- **Architecture**:
  - LSTM layer (128 units, return_sequences=True)
  - LSTM layer (64 units)
  - Dense layer (25 units)
  - Dense output layer (1 unit)
- **Training**: Model trained on historical stock data and saved as `.keras` file
- **Scaler**: MinMaxScaler for feature normalization (0-1 range)

## 🔐 API Endpoints

- `POST /api/register/` - User registration
- `POST /api/login/` - User login (returns JWT token)
- `GET /api/protected-view/` - Protected route (requires authentication)
- `POST /api/predict/` - Stock prediction endpoint
  - Request: `{ "ticker": "AAPL" }`
  - Response: Prediction plots, metrics (MSE, RMSE, R²)

## 🎯 Usage Example

1. Register a new account or login
2. Navigate to the dashboard
3. Enter a stock ticker symbol (e.g., "AAPL" for Apple Inc.)
4. Click "See Prediction"
5. View the generated charts and model evaluation metrics

## 📝 Notes

- The LSTM model (`stock_prediction_model.keras`) should be placed in the `backend-drf/api/` directory
- Ensure you have sufficient memory for loading and running the Keras model
- Stock data is fetched in real-time, so predictions depend on current market data availability

## 🔧 Development

### Running Tests
```bash
# Backend
cd backend-drf
python manage.py test

# Frontend
cd frontend-react
npm run lint
```

### Building for Production
```bash
# Frontend
cd frontend-react
npm run build
```

## 📄 License

This project is open source and available for educational purposes.

## 👤 Author

**Raj110123**

## 🙏 Acknowledgments

- yfinance for stock data API
- TensorFlow/Keras for deep learning capabilities
- Django REST Framework community
- React community

---

**Note**: Stock market predictions are for educational purposes only and should not be used as financial advice. Past performance does not guarantee future results.
