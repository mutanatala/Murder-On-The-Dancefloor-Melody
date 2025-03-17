# Murder-On-The-Dancefloor-Melody
import numpy as np
import simpleaudio as sa

def generate_tone(frequency, duration, sample_rate=44100):
    """Generate a sine wave tone."""
    t = np.linspace(0, duration, int(sample_rate * duration), False)
    wave = 0.5 * np.sin(2 * np.pi * frequency * t)
    return (wave * 32767).astype(np.int16)

def play_melody():
    """Play a simple melody inspired by Murder on the Dancefloor."""
    melody = [
        (440, 0.4),  # A4
        (493, 0.4),  # B4
        (523, 0.4),  # C5
        (587, 0.6),  # D5
        (523, 0.4),  # C5
        (440, 0.4),  # A4
        (392, 0.6),  # G4
        (440, 0.4),  # A4
    ]
    
    for freq, dur in melody:
        wave_obj = sa.WaveObject(generate_tone(freq, dur), 1, 2, 44100)
        play_obj = wave_obj.play()
        play_obj.wait_done()
    
if __name__ == "__main__":
    print("🎶 Playing a simple melody inspired by 'Murder on the Dancefloor'...")
    play_melody()
