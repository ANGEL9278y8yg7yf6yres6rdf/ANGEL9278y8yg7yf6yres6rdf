import pygame
import random

# Inicializar Pygame
pygame.init()

# Configuración de la pantalla
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Tetris")

# Definición de colores
colors = [
    (0, 0, 0),
    (0, 240, 240),
    (0, 0, 240),
    (240, 160, 0),
    (240, 240, 0),
    (0, 240, 0),
    (160, 0, 240),
    (240, 0, 0)
]

# Definición de formas
shapes = [
    [[1, 1, 1, 1]],
    [[2, 2],
     [2, 2]],
    [[0, 3, 0],
     [3, 3, 3]],
    [[4, 4, 0],
     [0, 4, 4]],
    [[0, 5, 5],
     [5, 5, 0]],
    [[6, 6, 6],
     [0, 6, 0]],
    [[7, 7, 7],
     [7, 0, 0]]
]

# Clase para las piezas del Tetris
class Piece:
    def __init__(self, x, y, shape):
        self.x = x
        self.y = y
        self.shape = shape
        self.color = colors[shapes.index(shape) + 1]
        self.rotation = 0

def create_grid(locked_positions={}):
    grid = [[(0, 0, 0) for x in range(10)] for y in range(20)]
    for y in range(20):
        for x in range(10):
            if (x, y) in locked_positions:
                c = locked_positions[(x, y)]
                grid[y][x] = c
    return grid

def draw_grid(surface, grid):
    sx = 300
    sy = 50
    for y in range(len(grid)):
        for x in range(len(grid[y])):
            pygame.draw.rect(surface, grid[y][x], (sx + x*30, sy + y*30, 30, 30), 0)

def draw_window(surface, grid):
    surface.fill((0, 0, 0))
    draw_grid(surface, grid)
    pygame.display.update()

# Función principal del juego
def main():
    locked_positions = {}
    grid = create_grid(locked_positions)

    run = True
    current_piece = Piece(5, 0, random.choice(shapes))

    while run:
        grid = create_grid(locked_positions)
        draw_window(screen, grid)

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False

main()
pygame.quit()


<!---
ANGEL9278y8yg7yf6yres6rdf/ANGEL9278y8yg7yf6yres6rdf is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
