#include <iostream>
#include <fstream>
#include <algorithm>
#include <vector>

using namespace std;

bool flag = true;
char harta[20][20];
void citeste();
struct punct
{
    int x, y;
};
bool operator==(punct p1, punct p2);
void afiseazaHarta();

int n, m;
punct I, F;

vector<punct> labirint(vector<punct> pozitii)
{
    int X = pozitii.back().x;
    int Y = pozitii.back().y;

    if (pozitii.back() == F)
    {
        throw pozitii;
    }

    else
    {

        if (harta[X][Y - 1] != '+')
        {
            punct temp;
            temp.x = X;
            temp.y = Y - 1;

            std::vector<punct>::iterator it;
            it = find(pozitii.begin(), pozitii.end(), temp);
            if (it == pozitii.end())
            {
                pozitii.push_back(temp);
                labirint(pozitii);
            }
        }
        if (harta[X][Y + 1] != '+')
        {
            punct temp;
            temp.x = X;
            temp.y = Y + 1;

            std::vector<punct>::iterator it;
            it = find(pozitii.begin(), pozitii.end(), temp);
            if (it == pozitii.end())
            {
                pozitii.push_back(temp);
                labirint(pozitii);
            }
        }
        if (harta[X - 1][Y] != '+')
        {
            punct temp;
            temp.x = X - 1;
            temp.y = Y;

            std::vector<punct>::iterator it;
            it = find(pozitii.begin(), pozitii.end(), temp);
            if (it == pozitii.end())
            {
                pozitii.push_back(temp);
                labirint(pozitii);
            }
        }
        if (harta[X + 1][Y] != '+')
        {
            punct temp;
            temp.x = X+1;
            temp.y = Y;

            std::vector<punct>::iterator it;
            it = find(pozitii.begin(), pozitii.end(), temp);
            if (it == pozitii.end())
            {
                pozitii.push_back(temp);
                labirint(pozitii);
            }
        }
        harta[X][Y] = '+';
        //afiseazaHarta();
        pozitii.pop_back();
        labirint(pozitii);
    }
}

int main()
{
    vector<punct> locatii;
    citeste();
    locatii.push_back(I);
    try
    {
        locatii = labirint(locatii);
    }
    catch (vector <punct> e) {

        cout << "Traseul corect este" << endl;

        for (int i = 0; i < e.size(); i++)
        {
            cout << e[i].x << " " << e[i].y << endl;
        }

    }


    return 0;
}

void citeste()
{
    fstream my_file;
    my_file.open("lab.txt", ios::in);
    my_file >> n >> m;

    my_file.get();

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        {
            my_file.get(harta[i][j]);
            if (harta[i][j] == 'I')
            {
                I.x = i;
                I.y = j;
            }

            if (harta[i][j] == 'F')
            {
                F.x = i;
                F.y = j;
            }
        }
        my_file.get();
    }

    my_file.close();
}

bool operator==(punct p1, punct p2)
{
    if (p1.x == p2.x && p1.y == p2.y)
        return true;
    else
        return false;
}


void afiseazaHarta()
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        {
            cout << harta[i][j];
        }
        cout << endl;
    }
}

/*
lab.txt
6 9
+++++++++
+     + +
+++I+++ +
+     +F+
+++ +   +
+++++++++
*/
