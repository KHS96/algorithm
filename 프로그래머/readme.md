#include <string>
#include <vector>
#include <cmath>
using namespace std;


string solution(vector<int> numbers, string hand) {
    string answer = "";
    int ypos[] = {4,1,1,1,2,2,2,3,3,3};
    int xpos[] = {2,1,2,3,1,2,3,1,2,3};
    int rx = 3;
    int ry = 4;
    int lx = 1;
    int ly = 4;
    for(int i = 0 ; i<numbers.size();i++)
    {
        if( numbers.at(i) == 1 || numbers.at(i) == 4 || numbers.at(i) == 7){
            answer += 'L';
            lx = xpos[numbers.at(i)];
            ly = ypos[numbers.at(i)];
        } else if(numbers.at(i) == 3 || numbers.at(i) == 6 || numbers.at(i) == 9){
            answer += 'R';
            rx = xpos[numbers.at(i)];
            ry = ypos[numbers.at(i)];
        } else if(numbers.at(i) == 2 || numbers.at(i) == 5 || numbers.at(i) == 8 || numbers.at(i) == 0){
            if ( abs(rx-xpos[numbers.at(i)]) + abs(ry-ypos[numbers.at(i)]) > abs(lx-xpos[numbers.at(i)]) + abs(ly-ypos[numbers.at(i)]) ){
                answer+='L';
                lx = xpos[numbers.at(i)];
                ly = ypos[numbers.at(i)];
            } else if (abs(rx-xpos[numbers.at(i)]) + abs(ry-ypos[numbers.at(i)]) < abs(lx-xpos[numbers.at(i)]) + abs(ly-ypos[numbers.at(i)]) ){
                answer+='R';
                rx = xpos[numbers.at(i)];
                ry = ypos[numbers.at(i)];
            } else {
                if(hand == "right")
                {
                    answer+='R';
                    rx = xpos[numbers.at(i)];
                    ry = ypos[numbers.at(i)];
                }else {
                    answer+='L';
                    lx = xpos[numbers.at(i)];
                    ly = ypos[numbers.at(i)];
                }
            }
        }
    }
    
    return answer;
}
                
