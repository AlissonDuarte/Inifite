import pygame
import sys

# Configurações
WIDTH, HEIGHT = 800, 600
INITIAL_SCALE = 1.0
ZOOM_FACTOR = 1.2
MAX_ITERATIONS = 100

def mandelbrot(c):
    z = 0
    n = 0
    while abs(z) <= 2 and n < MAX_ITERATIONS:
        z = z*z + c
        n += 1
    return n

def main():
    pygame.init()
    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    clock = pygame.time.Clock()

    scale = INITIAL_SCALE
    offset_x, offset_y = 0, 0

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            elif event.type == pygame.MOUSEBUTTONDOWN:
                if event.button == 4:  # Scroll up
                    scale *= ZOOM_FACTOR
                elif event.button == 5:  # Scroll down
                    scale /= ZOOM_FACTOR

        for y in range(HEIGHT):
            for x in range(WIDTH):
                zx = (x - WIDTH / 2) / scale + offset_x
                zy = (y - HEIGHT / 2) / scale + offset_y
                c = zx + zy * 1j
                color = mandelbrot(c)
                pygame.draw.rect(screen, (color % 256, color % 256, color % 256), (x, y, 1, 1))

        pygame.display.flip()
        clock.tick(30)

    pygame.quit()
    sys.exit()

if __name__ == "__main__":
    main()

