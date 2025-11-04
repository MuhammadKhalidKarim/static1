from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def home():
    return "Welcome to My Flask App!"

@app.route('/about')
def about():
    return "This is a simple Flask app for Codacy analysis."

@app.route('/add', methods=['GET', 'POST'])
def add():
    if request.method == 'POST':
        try:
            a = int(request.form['a'])
            b = int(request.form['b'])
            return f"Sum: {a + b}"
        except Exception as e:
            return f"Error: {str(e)}"
    return '''
        <form method="post">
            <input name="a" placeholder="Enter first number"><br>
            <input name="b" placeholder="Enter second number"><br>
            <input type="submit" value="Add">
        </form>
    '''

if __name__ == '__main__':
    app.run(debug=True)
