#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_BALLS 5
#define BOARD_WIDTH 10
#define BOARD_HEIGHT 10

typedef struct {
    int x;
    int y;
} Ball;

typedef struct {
    Ball balls[MAX_BALLS];
    int num_balls;
} Board;

void initialize_board(Board *board) {
    board->num_balls = MAX_BALLS;
    srand(time(NULL));
    for (int i = 0; i < board->num_balls; i++) {
        board->balls[i].x = rand() % BOARD_WIDTH;
        board->balls[i].y = rand() % BOARD_HEIGHT;
    }
}

void print_board(Board *board) {
    for (int y = 0; y < BOARD_HEIGHT; y++) {
        for (int x = 0; x < BOARD_WIDTH; x++) {
            char is_ball = ' ';
            for (int i = 0; i < board->num_balls; i++) {
                if (board->balls[i].x == x && board->balls[i].y == y) {
                    is_ball = 'O';
                    break;
                }
            }
            printf("%c ", is_ball);
        }
        printf("\n");
    }
}

int main() {
    Board board;
    initialize_board(&board);
    print_board(&board);
    return 0;
}
# cxlk
