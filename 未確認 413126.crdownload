from browser import document as doc
from browser import html
import math

GLOBAL_CANVAS = html.CANVAS(width = 600, height = 400, style="border: 1px solid #ccc;")
GLOBAL_CANVAS.id = "taiwan_flag_canvas"

try:
    doc["brython_div1"] <= GLOBAL_CANVAS
except KeyError:
    print("找不到 bry典範div1。嘗試使用預設執行畫布。")
    pass

MAIN_CANVAS = doc["taiwan_flag_canvas"]
ctx = MAIN_CANVAS.getContext("2d")

F_WIDTH = 400
F_HEIGHT = 260
SUN_X = F_WIDTH / 4
SUN_Y = F_HEIGHT / 4

def draw_flag_pattern():
    ctx.fillStyle = 'rgb(255, 0, 0)'
    ctx.fillRect(0, 0, F_WIDTH, F_HEIGHT)

    ctx.fillStyle = 'rgb(0, 0, 150)'
    ctx.fillRect(0, 0, F_WIDTH / 2, F_HEIGHT / 2)

    ctx.beginPath()
    RAY_RAD = F_WIDTH / 8
    ANGLE_STEP_RAD = 15 * math.pi / 180
    
    for i in range(24):
        angle = ANGLE_STEP_RAD * i
        
        if i % 2 == 0:
            CURRENT_RAD = RAY_RAD
        else:
            CURRENT_RAD = RAY_RAD * 0.4
            
        TARGET_X = SUN_X + math.cos(angle) * CURRENT_RAD
        TARGET_Y = SUN_Y + math.sin(angle) * CURRENT_RAD
        
        if (i == 0):
            ctx.moveTo(TARGET_X, TARGET_Y)
        else:
            ctx.lineTo(TARGET_X, TARGET_Y)
            
    ctx.closePath()
    ctx.fillStyle = '#fff'
    ctx.fill()

    ctx.beginPath()
    BLUE_RAD = F_WIDTH * 17 / 240
    ctx.arc(SUN_X, SUN_Y, BLUE_RAD, 0, math.pi * 2)
    ctx.closePath()
    ctx.fillStyle = 'rgb(0, 0, 149)'
    ctx.fill()

    ctx.beginPath()
    WHITE_RAD = F_WIDTH / 16
    ctx.arc(SUN_X, SUN_Y, WHITE_RAD, 0, math.pi * 2)
    ctx.closePath()
    ctx.fillStyle = '#fff'
    ctx.fill()

CENTER_1_X = 180
CENTER_2_X = 420
CENTER_Y = 200
S_FACTOR = 0.65

ctx.save()
ctx.translate(CENTER_1_X, CENTER_Y)
ctx.rotate(math.radians(45))
ctx.scale(S_FACTOR, S_FACTOR)
ctx.translate(-F_WIDTH / 2, -F_HEIGHT / 2)
draw_flag_pattern()
ctx.restore()

ctx.save()
ctx.translate(CENTER_2_X, CENTER_Y)
ctx.rotate(math.radians(90))
ctx.scale(S_FACTOR, S_FACTOR)
ctx.translate(-F_WIDTH / 2, -F_HEIGHT / 2)
draw_flag_pattern()
ctx.restore()