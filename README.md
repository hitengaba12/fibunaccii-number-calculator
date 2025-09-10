import speech_recognition as sr
import webbrowser
import pyttsx3 
import time
# import musiclibrary
# Initialize recognizer and text-to-speech engine
recognizer = sr.Recognizer()
tts = pyttsx3.init()

# Function to speak text
def speak(text):
    tts.say(text)
    tts.runAndWait()
def processcommand(c):
    
    if c.lower()=="open google" in c.lower():
        webbrowser.open("https://google.com")
    elif c.lower()=="open youtube" in c.lower():
        webbrowser.open("https://youtube.com")
    elif c.lower()=="open instagram" in c.lower():
        webbrowser.open("https://instagram.com")
    # elif c.lower().startswith("play"):
    #     song=c.lower().split(" ")[1]
    #     link= music.music[song]
    #     webbrowser.open(link)
if __name__ == "__main__":
    speak("initializing jarvis.... ")
    while True:
        r = sr.Recognizer()
        print("Starting... (say something)", flush=True)
        print("recognizing...")

        try:
            with sr.Microphone() as source:
                print("Say something!")
                recognizer.adjust_for_ambient_noise(source, duration=1)

                audio = recognizer.listen(source)
                word=recognizer.recognize_google(audio)
                print("you said",word)
                
            if "jarvis" in word.lower():
                time.sleep(0.3)
                speak("jarvis active")
                with sr.Microphone() as source:
                    print("jarvis active...")
                    
                    audio = recognizer.listen(source)
                command= recognizer.recognize_google(audio)
                processcommand(command)
        except Exception as e:
            print("error; {0}".format(e))
      
