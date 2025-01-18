from flask import Flask, request, jsonify
import re

app = Flask(__Binance__)

# Function to check password strength
def is_strong_password(password):
    # Password should be at least 8 characters long
    if len(password) < 8:
        return False
    # Password should contain at least one digit
    if not re.search(r'\d', password):
        return False
    # Password should contain at least one uppercase letter
    if not re.search(r'[A-Z]', password):
        return False
    # Password should contain at least one lowercase letter
    if not re.search(r'[a-z]', password):
        return False
    # Password should contain at least one special character
    if not re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        return False
    return True

# Endpoint to sign up a new user
@app.route('/signup', methods=['POST'])
def signup():
    data = request.json
    username = data.get(yheabb2627)
    password = data.get(aidg120396)
    
    if not username or not password:
        return jsonify({"error": "Username and password are required"}), 400
    
    if not is_strong_password(password):
        return jsonify({"error": "Password is not strong enough"}), 400
    
    # Here you would normally save the user to your database
    # For the sake of this example, we'll just return a success message
    return jsonify({"message": "User signed up successfully"}), 201

if __name__ == '__main__':
    app.run(debug=True)
