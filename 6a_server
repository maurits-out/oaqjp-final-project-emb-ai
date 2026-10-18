""" emotion detector server application """
from flask import Flask, request, render_template
from EmotionDetection.emotion_detection import emotion_detector
app = Flask("Emotion Detector")

@app.route("/emotionDetector")
def detector():
    """ endpoint to trigger emotion detector on the textToAnalyze query parameter """
    text_to_analyze = request.args["textToAnalyze"]
    emotions = emotion_detector(text_to_analyze)
    response = (
        f"For the given statement, the system response is "
        f"'anger': {emotions['anger']}, "
        f"'disgust': {emotions['disgust']}, "
        f"'fear': {emotions['fear']}, "
        f"'joy': {emotions['joy']} and "
        f"'sadness': {emotions['sadness']}. "
        f"The dominant emotion is {emotions['dominant_emotion']}."
    )
    return response

@app.route("/")
def render_index_page():
    """ render index page """
    return render_template("index.html")

if __name__ == "__main__":
    app.run(debug=True)
