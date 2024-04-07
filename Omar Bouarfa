//#include <stdio.h>
#include <allegro.h>
#include <stdbool.h>



typedef struct {
    int x1, y1, x2, y2; // Coordonnées du coin supérieur gauche (x1, y1) et du coin inférieur droit (x2, y2)
} Rectangle;

bool is_inside(Rectangle r, int x, int y) {
    return (x >= r.x1 && x <= r.x2 && y >= r.y1 && y <= r.y2);
}


int main() {
    allegro_init();
    install_keyboard();
    int result = install_mouse();
    if (install_mouse() == -1) {
        allegro_message("Erreur ! %s", allegro_error);
        return 1;
    }
    set_color_depth(desktop_color_depth());
    if(set_gfx_mode(GFX_AUTODETECT_WINDOWED,640, 480, 0,0)!=0){
        set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
        allegro_message("Impossible d'initialiser le mode video");
        return 1;
    }
    show_mouse(screen);

    BITMAP *image1 = load_bitmap("C:\\Users\\omarb\\Downloads\\over_cooked\\overcooked_image.bmp", NULL);
    if (!image1) {
        set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
        allegro_message("Impossible de charger l'image");
        return 1;
    }
    blit(image1, screen, 0, 0, 0, 0, image1->w, image1->h);
    while (!keypressed() || (readkey() >> 8) != KEY_SPACE) {}



    BITMAP *image2 = load_bitmap("C:\\Users\\omarb\\Downloads\\over_cooked\\image_menu.bmp", NULL);
    if (!image2) {
        set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
        allegro_message("Impossible de charger l'image 2");
        destroy_bitmap(image1);
        return 1;
    }

    // Afficher la deuxième image
    blit(image2, screen, 0, 0, 0, 0, image2->w, image2->h);

    Rectangle startRect = {233, 288, 420, 317};

    while (true) {
        // Détecter le clic de souris
        if (mouse_b & 1) {
            int mouseX = mouse_x;
            int mouseY = mouse_y;
            // Vérifier si le clic est à l'intérieur du rectangle "Start"
            if (is_inside(startRect, mouseX, mouseY)) {
                // Remplir l'écran d'une couleur noire
                clear_to_color(screen, makecol(0, 0, 0));
                break; // Sortir de la boucle si le clic est dans le rectangle "Start"
            }
        }
    }

    // Remplir l'écran d'une couleur noire
    clear_to_color(screen, makecol(0, 0, 0));

    // Attendre jusqu'à ce qu'une autre touche soit enfoncée
    readkey();
    destroy_bitmap(image2);
    return 0;
}
END_OF_MAIN()


// x1 = 233 X2 = 420 y1= 288 y2 = 317
