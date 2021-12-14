#include <opencv2/core/core.hpp>
#include <opencv2/highgui/highgui.hpp>
#include <opencv2/imgproc.hpp>
#include <iostream>
#include <vector>

int main()
{
    std::vector<double> x;
    std::vector<double> y;
    int n = 1000;
    double sumx = 0, sumy = 0, sumxx = 0, sumyy = 0, sumxy = 0;
    
    cv::Mat IG1 = cv::Mat::zeros(700, 1000, CV_8UC3);cv::Vec3b color;
    color[0] = 255;
    color[1] = 0;
    color[2] = 0;

    for (int i = 0; i < 2; i++) {
    
        //Use random x and y as an example
        x.push_back(rand() % 800);
        y.push_back(0.5 * x[i] + rand() % 100 - 50);
        
        cv::circle(IG1, cv::Point(x[i] + 100, 600 - y[i]), 2, cv::Scalar(0, 255, 0), -100);

        n = n + 1;
        sumx = sumx + x[i];
        sumy = sumy + y[i];
        sumxx = sumxx + x[i] * x[i];
        sumxy = sumxy + x[i] * y[i];
    }

    cv::namedWindow("Display Window");
    cv::imshow("Display Window", IG1);
    cv::waitKey(0);

    double k = (sumx * sumy - n * sumxy) / (sumx * sumx - n * sumxx);
    double b = (sumy - sumx * k) / n;
    std::cout << "Estimation is y = " << b << " + " << k << "x";
    cv::Point p0(100, 600 - b), p1(100 + 800, int(600 - k * 800 - b));
    cv::line(IG1, p0, p1, cv::Scalar(255, 0, 255), 1);

    cv::imshow("Display Window", IG1);
    cv::waitKey(0);

    return 0;
}
