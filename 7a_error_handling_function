""" Provides functionality to detect emotion from a text """
import json
import requests

def empty_emotion():
    """ returns emotion dictonary with all keys being None """
    emotion = {}
    for key in ["anger", "disgust", "fear", "joy", "sadness", "dominant_emotion"]:
        emotion[key] = None
    return emotion

def parse_response_text(text):
    """ parse the response into an emotion dictionary """
    formatted_response = json.loads(text)
    emotion = formatted_response["emotionPredictions"][0]["emotion"]
    emotion["dominant_emotion"] = max(emotion, key = emotion.get)
    return emotion

def emotion_detector(text_to_analyze):
    """ Runs emotion detection on the supplied text """
    url = (
        "https://sn-watson-emotion.labs.skills.network"
        "/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict"
    )
    headers = { "grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock" }
    body = { "raw_document": { "text": text_to_analyze } }
    response = requests.post(url, json = body, headers = headers, timeout = 10)
    if response.status_code == 400:
        return empty_emotion()
    return parse_response_text(response.text)
