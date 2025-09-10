from moviepy.editor import ImageClip, concatenate_videoclips, TextClip, CompositeVideoClip

# Fotos que você enviou (coloque os nomes/endereços corretos dos arquivos)
fotos = [
    "foto1.jpg", "foto2.jpg", "foto3.jpg",
    "foto4.jpg", "foto5.jpg", "foto6.jpg", "foto7.jpg"
]

# Frases que vão aparecer
frases = [
    "Meu maior presente é ter você na minha vida ❤️",
    "A dona do sorriso mais lindo do mundo ✨",
    "Seus cachos são poesia que até o vento admira 🌸",
    "Hoje é o seu dia, mas quem comemora sou eu 🎉",
    "Te amo mais do que consigo explicar 💍",
    "Feliz Aniversário, meu amor – 10/10 ❤️"
]

clips = []
duracao_foto = 4  # cada foto fica 4s na tela

for i, foto in enumerate(fotos):
    img = ImageClip(foto).set_duration(duracao_foto).resize(height=1920).resize(width=1080).set_position("center")

    if i < len(frases):
        txt = TextClip(frases[i], fontsize=60, color="white", font="Arial-Bold", method="caption", size=(900, None))
        txt = txt.set_duration(duracao_foto).set_position(("center", "bottom"))
        clip = CompositeVideoClip([img, txt])
    else:
        clip = img

    clips.append(clip)

final = concatenate_videoclips(clips, method="compose")
final.write_videofile("video_namorada.mp4", fps=24)

👉 Resultado: um vídeo vertical de ~30s, com as 7 fotos + frases. Depois é só postar no Instagram e colocar a música do Oruam.
