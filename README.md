# 7X7-matric
def spiral_matrix(n):
    # 7x7 o'lchamli bo'sh matritsa yaratamiz
    matrix = [[0] * n for _ in range(n)]
    
    # Spiral harakat uchun chegaralarni belgilash
    top, bottom, left, right = 0, n - 1, 0, n - 1
    num = 1  # Matritsani to'ldiradigan qiymat

    while top <= bottom and left <= right:
        # Yuqoridan chapdan o‘ngga harakat
        for i in range(left, right + 1):
            matrix[top][i] = num
            num += 1
        top += 1

        # O‘ngdan yuqoridan pastga harakat
        for i in range(top, bottom + 1):
            matrix[i][right] = num
            num += 1
        right -= 1

        # Pastdan o‘ngdan chapga harakat (agar past qator qolgan bo'lsa)
        if top <= bottom:
            for i in range(right, left - 1, -1):
                matrix[bottom][i] = num
                num += 1
            bottom -= 1

        # Chapdan pastdan yuqoriga harakat (agar chap ustun qolgan bo'lsa)
        if left <= right:
            for i in range(bottom, top - 1, -1):
                matrix[i][left] = num
                num += 1
            left += 1

    return matrix


# Matritsani to'ldirish va chop etish
n = 7
result = spiral_matrix(n)
for row in result:
    print(row)
