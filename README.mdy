from ursina import *
from ursina.prefabs.first_person_controller import FirstPersonController

app = Ursina()

# Создаем свой класс блока
class Voxel(Button):
    def __init__(self, position=(0,0,0)):
        super().__init__(
            parent=scene,
            model='cube',
            texture='white_cube',
            position=position,
            highlight_color=color.lime,  # Цвет подсветки при наведении
            color=color.white
        )

    # Функция, которая вызывается при нажатии на блок
    def input(self, key):
        if self.hovered:
            if key == 'left mouse down':    # ЛКМ - разрушить блок
                destroy(self)
            if key == 'right mouse down':   # ПКМ - создать новый блок рядом
                Voxel(position=self.position + mouse.normal)

# Генерируем пол из наших новых блоков
for x in range(16):
    for z in range(16):
        Voxel(position=(x, 0, z))

player = FirstPersonController()
player.gravity = 0.0

app.run()
