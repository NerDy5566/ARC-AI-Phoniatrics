# ARC-AI-Phoniatrics
Articulation disorder is a common language problem in children, resulting in incorrect bite and unclear sentences. At present, there is no unified definition of the types of dysarthria in the medical profession in Taiwan. speech therapist must be provided in hospital treatment. After a series of pronunciation of the words, the therapist will make judgments based on the child’s pronunciation, and will continue to visit for several months to improve the pronunciation problems. This will cause the patient’s treatment cycle to be lengthened and the patient can only be treated in the hospital. We hope to automate the treatment process, use the phonetic character cards used in major hospitals as the basis for judgment, and combine the convolutional neural network in machine learning to classify several types of phonological errors and correct categories.

**Enviroment: Python 3.8
Demo on Himax WE-I Plus EVB Endpoint AI Development Board**

We collocate 15 types of Articulation disorder and non-Articulation disorder voice for this classifaction.
On the original Trainning have a great performance, but we wish it can run on the embedded-system use TFLite Model.

The original model is used to support doctor to check the pantient's pronunciation is right or not
And this project is for the familly to check the baby wheather have Articulation disorder or not ,so we want it run on the embedded-system.

Because we need to run on the embedded-system, we need to shrink the original model and function.
In the test, we need to sort the result for the two type ("Right", "False") for the smaller size for the embedded-system.


Code Explain:
  
  First we need to prepare for the trainning dataset.
  
  '''python3.7
  def read_audio_from_filename(filename, target_sr, ori_sr):
    audio, _ = librosa.load(filename, sr=ori_sr, mono=True)
    audio_target_sr = librosa.resample(y=audio, orig_sr=_, target_sr=target_sr) # ori_sr to target_sr
    audio_target_sr = audio_target_sr.reshape(-1, 1)
    #print(audio.shape)
    #print(audio_target_sr.shape)
    return audio_target_sr
  '''
