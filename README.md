# To get speech up and running:

  # Mac
  
  sudo pip3 install espeak pyttsx pydub gTTS SpeechRecognition 

  brew install ffmpeg 
  brew install portaudio
  
  <b><i>From inside directory</i></b>
  
  cd src/pyaudio
  sudo python setup.py install
  
  
  # Linux 
  
  sudo pip3 install pyttsx gTTS pydub SpeechRecognition 
  sudo apt-get install espeak 
  sudo apt-get install ffmpeg
  
  <b><i>From inside directory</i></b> 
  
  cd src/pyaudio
  sudo python setup.py install
  
  sudo apt-get installl libportaudio-dev
  sudo apt-get install python-dev
  sudo apt-get install libportaudio0 libportaudio2 libportaudiocpp0 portaudio19-dev

# Voices & Linux Support

The code is set up to run out of the box on Mac, but with linux you will need to add in the reference to the voice model (I find they sound far more robotic than Apple's though) You can also use this script to find the other voices on Mac. 

import pyttsx3
engine = pyttsx3.init()

voices = engine.getProperty('voices')
for voice in voices:
    print("Voice:")
    print(" - ID: %s" % voice.id)
    print(" - Name: %s" % voice.name)
    print(" - Languages: %s" % voice.languages)
    print(" - Gender: %s" % voice.gender)
    print(" - Age: %s" % voice.age)
    
 It will print a long list like this one (done on Mac)
 
      Voice:
       - ID: com.apple.speech.synthesis.voice.Alex <---- you copy this 
       
      Voice:
       - ID: com.apple.speech.synthesis.voice.alice
       
      Voice:
       - ID: com.apple.speech.synthesis.voice.alva
       
      Voice:
       - ID: com.apple.speech.synthesis.voice.amelie
       
      Voice:
       - ID: com.apple.speech.synthesis.voice.anna

    
Next, you will go the "interactive_conditional_samples.py" file and edit line 19 to paste the path for the voice model

# This is what you can expect from the command line 

<img src="https://i.imgur.com/4cMKifz.png"></img>

# Remember to download the models as instructed below - setup is the same)

# gpt-2

Code from the paper ["Language Models are Unsupervised Multitask Learners"](https://d4mucfpksywv.cloudfront.net/better-language-models/language-models.pdf).

We have currently released small (124M parameter), medium (355M parameter), and large (774M parameter) versions of GPT-2<sup>*</sup>, with only the full model as of yet unreleased.  We have also [released a dataset](https://github.com/openai/gpt-2-output-dataset) for researchers to study their behaviors.

You can read about GPT-2 and release decisions in our [original blog post](https://blog.openai.com/better-language-models/) and [6 month follow-up post](https://openai.com/blog/gpt-2-6-month-follow-up/).

<sup>*</sup> *Note that our original parameter counts were wrong due to an error (in our previous blog posts and paper).  Thus you may have seen small referred to as 117M and medium referred to as 345M.*

## Usage

This repository is meant to be a starting point for researchers and engineers to experiment with GPT-2.

For basic information, see our [model card](./model_card.md).

### Some caveats

- GPT-2 models' robustness and worst case behaviors are not well-understood.  As with any machine-learned model, carefully evaluate GPT-2 for your use case, especially if used without fine-tuning or in safety-critical applications where reliability is important.
- The dataset our GPT-2 models were trained on contains many texts with [biases](https://twitter.com/TomerUllman/status/1101485289720242177) and factual inaccuracies, and thus GPT-2 models are likely to be biased and inaccurate as well.
- To avoid having samples mistaken as human-written, we recommend clearly labeling samples as synthetic before wide dissemination.  Our models are often incoherent or inaccurate in subtle ways, which takes more than a quick read for a human to notice.

### Work with us

Please [let us know](mailto:languagequestions@openai.com) if you’re doing interesting research with or working on applications of GPT-2!  We’re especially interested in hearing from and potentially working with those who are studying
- Potential malicious use cases and defenses against them (e.g. the detectability of synthetic text)
- The extent of problematic content (e.g. bias) being baked into the models and effective mitigations

## Development

See [DEVELOPERS.md](./DEVELOPERS.md)

## Contributors

See [CONTRIBUTORS.md](./CONTRIBUTORS.md)

## Citation

Please use the following bibtex entry:
```
@article{radford2019language,
  title={Language Models are Unsupervised Multitask Learners},
  author={Radford, Alec and Wu, Jeff and Child, Rewon and Luan, David and Amodei, Dario and Sutskever, Ilya},
  year={2019}
}
```

## Future work

We may release code for evaluating the models on various benchmarks.

We are still considering release of the larger models.

## License

[MIT](./LICENSE)
