import random
import numpy as np
import matplotlib.pyplot as plot

EPSILON = 0.01  # Represents the range of admitted errors when nearing the min point
LAMBDA = 50  # Represents the maximum number of steps the descent should have in order to find the min point
LATEST_ELEMENT = -1
X_SPOT = 0
Y_SPOT = 1
CHART_BOUND = 100  # Should always be a positive integer


def f(x, y, y_coefficient):
    return (1 / 2) * ((x ** 2) + y_coefficient * (y ** 2))


def gradient_f(x, y, y_coefficient):
    return x, y_coefficient * y


def step(x, y, y_coefficient):
    partial = (y_coefficient ** 3) * (y ** 2)
    return 1 - ((partial - ((y_coefficient * y) ** 2)) / (partial + (x ** 2)))


def next_step(x, y, y_coefficient):
    s = step(x, y, y_coefficient)
    return x * (1 - s), y * (1 - y_coefficient * s)


def descend(x_start, y_start, y_coefficient):
    x = [x_start]
    y = [y_start]
    dfdx, dfdy = gradient_f(x_start, y_start, y_coefficient)
    while (abs(dfdx) >= EPSILON or abs(dfdy) >= EPSILON) and len(x) <= LAMBDA:
        next_x, next_y = next_step(x[LATEST_ELEMENT], y[LATEST_ELEMENT], y_coefficient)
        x.append(next_x)
        y.append(next_y)
        dfdx, dfdy = gradient_f(x[LATEST_ELEMENT], y[LATEST_ELEMENT], y_coefficient)
    return x, y


def show_data_points(x_list, y_list, y_coefficient):
    print("b ==", y_coefficient)
    for index in range(len(x_list)):
        print(index + 1, ". ", x_list[index], ", ", y_list[index], "-> ",
              f(x_list[index], y_list[index], y_coefficient))


def plot_descent(x_start, y_start, y_coefficient):
    x_descent, y_descent = descend(x_start, y_start, y_coefficient)
    show_data_points(x_descent, y_descent, y_coefficient)

    x_space = np.linspace(-1 * CHART_BOUND, CHART_BOUND + 0.1, 100)
    y_space = np.linspace(-1 * CHART_BOUND, CHART_BOUND + 0.1, 100)
    x_val, y_val = np.meshgrid(x_space, y_space)
    z_val = f(x_val, y_val, y_coefficient)
    levels = []
    for k in range(len(x_descent)):
        levels.append(f(x_descent[k], y_descent[k], y_coefficient))
    levels = np.sort(levels)
    contours = plot.contour(x_val, y_val, z_val, levels, colors='black')
    plot.clabel(contours, inline=True, fontsize=8)
    plot.plot(x_descent, y_descent, 'r--o')
    plot.title("b == " + str(y_coefficient) + " (" + str(len(x_descent)) + " steps)")
    plot.show()


if __name__ == "__main__":
    for b in [1, 1 / 2, 1 / 5, 1 / 10]:
        plot_descent(random.randint(-1 * CHART_BOUND + (CHART_BOUND // 2), CHART_BOUND - (CHART_BOUND // 2)),
                     random.randint(-1 * CHART_BOUND + (CHART_BOUND // 2), CHART_BOUND - (CHART_BOUND // 2)), b)
