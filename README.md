- 👋 Hi, I’m @carolinamustrangi


<!---
carolinamustrangi/carolinamustrangi is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->


using Plots
using LaTeXStrings

pyplot(dpi=300)


f(x) = log(x)
df(x) = 1 / x


# Evaluate relative error between an approximation and exact value
function relative_error(approx, exact)
    return abs((approx - exact) / exact)
end


# Evaluate an approximation of func derivative at a point
function centered_diff(func, x, h)
    return 0.5 * (func(x + h) - func(x - h)) / h
end


exponents = LinRange(-1, -14, 28)
h_values = 10.0.^exponents

point = 25.0
best_h = 40.7283 * eps(1.0)^(1/3)



