# asignment3
//The asignment3 of Academic Writing, Norms, and Ethics（c语言使用牛顿法找到函数 f(x) = x^2 - 4 的根）;
#include <stdio.h>
#include <math.h>

// 目标函数;
double target_function(double x) {
    return x * x - 4;
}

// 目标函数的导数;
double derivative_function(double x) {
    return 2 * x;
}

// 牛顿法函数;
double newton_method(double (*f)(double), double (*df)(double), double x0, double tol, int max_iter) {
    double x = x0;
    int iter_count = 0;

    while (fabs(f(x)) > tol && iter_count < max_iter) {
        x = x - f(x) / df(x);
        iter_count++;
    }

    printf("迭代次数: %d\n", iter_count);
    return x;
}

int main() {
    double initial_guess = 3.0;
    double tolerance = 1e-6;
    int max_iterations = 100;

    double root = newton_method(target_function, derivative_function, initial_guess, tolerance, max_iterations);

    printf("牛顿法找到的根为: %lf\n", root);

    return 0;
}
