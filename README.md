# Testtriangle
import unittest


def classify_triangle(a, b, c):
    """
    a, b, c: Lengths of the sides of the triangle

    Output:
    A string specifying the type of triangle (equilateral, isosceles, scalene) and whether it is a right triangle or not.
    """

    if a <= 0 or b <= 0 or c <= 0:
        return "Invalid triangle"
    if a == b == c:
        return "Equilateral"
    elif a == b or b == c or a == c:
        if a * a + b * b == c * c or b * b + c * c == a * a or a * a + c * c == b * b:
            return "Isosceles and Right"
        else:
            return "Isosceles"
    elif a * a + b * b == c * c or b * b + c * c == a * a or a * a + c * c == b * b:
        return "Scalene and Right"
    else:
        return "Scalene"


class TestClassifyTriangle(unittest.TestCase):
    def test_equilateral_triangle(self):
        self.assertEqual(classify_triangle(3, 3, 3), "Equilateral")

    def test_isosceles_triangle(self):
        self.assertEqual(classify_triangle(3, 4, 5), "Isosceles")

    def test_scalene_triangle(self):
        self.assertEqual(classify_triangle(3, 4, 6), "Scalene")

    def test_right_triangle(self):
        self.assertEqual(classify_triangle(3, 5, 5), "Scalene and Right")

    def test_invalid_triangle(self):
        self.assertEqual(classify_triangle(0, 3, 5), "Invalid triangle")


if __name__ == "__main__":
    unittest.main()
