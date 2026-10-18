import unittest
from EmotionDetection.emotion_detection import emotion_detector

class TestEmotionDetector(unittest.TestCase):

    def assert_dominant_emotion(self, statement, expected):
        emotions = emotion_detector(statement)
        self.assertEqual(expected, emotions["dominant_emotion"])

    def test_emotion_detector(self):
        self.assert_dominant_emotion("I am glad this happened", "joy")
        self.assert_dominant_emotion("I am really mad about this", "anger")
        self.assert_dominant_emotion("I feel disgusted just hearing about this", "disgust")
        self.assert_dominant_emotion("I am so sad about this", "sadness")
        self.assert_dominant_emotion("I am really afraid that this will happen", "fear")
    
if __name__ == '__main__':
    unittest.main()
