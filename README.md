- 👋 Hi, I’m @carolinamustrangi
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

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

approxs = centered_diff.(f, point, h_values)
best_approx = centered_diff(f, point, best_h)

correct_places = -log10.(relative_error.(approxs, df(point)))
best_correct_places = -log10(relative_error(best_approx, df(point)))

plot(
    h_values,
    correct_places,
    xaxis=:log10,
    label="",
    marker=:c,
    xlabel=L"$h$",
    ylabel="Casas decimais corretas",
    xticks=[1e-14,1e-12,1e-10,1e-8,1e-6,1e-4,1e-2],
    linecolor="#0065d9",
    markercolor="#0065d9",
    markerstrokecolor="#0053b3"
)
plot!(
    [best_h],
    [best_correct_places],
    label=L"Melhor $h$",
    marker=:c,
    linecolor="#ffaaaa",
    markercolor="#8c00c7",
    markerstrokecolor="#5c0096"
)
title!("Precisão do método da diferença centrada")

savefig("plot.png")
