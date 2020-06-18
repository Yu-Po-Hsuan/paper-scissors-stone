**剪刀-石頭-布,外加黑白配**
```c++
#include <iostream>
#include <string>
#include <cstdlib>  
#include <ctime>
using namespace std;

//玩家類別
class Player
{
public:
        // 預設建構子
	Player();
        //玩家姓名暫定為"none"
	Player(string);
        //設定玩家姓名
	void scorePlus();
        //玩家分數加1
	int getScore();
        //取得玩家目前分數
	void setNmae(string);
        //重新設定玩家姓名
	void resetScore();
        //將玩家分數歸零
	string toString();
        //回傳玩家姓名
private:
        // 資料欄位(data fields) 為 private，分別有玩家姓名,初值為0的分數
	string name;
	int score = 0;
};

Player::Player()
{
	name = "none";
}
Player::Player(string n)
{
	this->name = n;
}
void Player::scorePlus()
{
	score++;
}
int Player::getScore()
{
	return score;
}
void Player::setNmae(string n)
{
	this->name = n;
}
void Player::resetScore()
{
	score = 0;
}
string Player::toString()
{
	return name;
}
---------------------------------------
//電腦類別
class Bot
{
public:
        // 預設建構子
	Bot();
        //直接賦予電腦姓名"computer"
	void scorePlus();
        //電腦分數加1
	int getScore();
        //取得電腦目前分數
	void resetScore();
        //將電腦分數歸零
	string toString();
        //回傳"computer"
private:
        // 資料欄位(data fields) 為 private，分別有"computer",初值為0的分數
	string name;
	int score=0;
};

Bot::Bot()
{
	name = "computer";
}
void Bot::scorePlus()
{
	score++;
}
int Bot::getScore() 
{
	return score;
}
void Bot::resetScore()
{
	score = 0;
}
string Bot::toString()
{
	return "Computer";
}
---------------------------------------
//main
//黑白配函式之玩家回合
void achi(int n,Player p,Bot b) {
	int com3;
	com3 = 1 + rand() % 4;
	if (n == com3) {
		switch (com3) {
		case 1:
			cout << "電腦頭向上,你贏了" << endl;
			p.scorePlus();
                      //玩家贏了,分數+1
			cout <<"目前比數: \n"<< b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數
			break;
		case 2:
			cout << "電腦頭向下,你贏了" << endl;
			p.scorePlus();
                      //玩家贏了,分數+1      
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數      
			break;
		case 3:
			cout << "電腦頭向左,你贏了" << endl;
                      //玩家贏了,分數+1      
			p.scorePlus();
                      //顯示目前電腦以及玩家目前的比數        
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
			break;
		case 4:
			cout << "電腦頭向右,你贏了" << endl;
                      //玩家贏了,分數+1
			p.scorePlus();
                      //顯示目前電腦以及玩家目前的比數  
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
			break;
		}
	}
	else {
		switch (com3) {
		case 1:
			cout << "電腦頭向上,沒輸沒贏,重來" << endl;
			break;
		case 2:
			cout << "電腦頭向下,沒輸沒贏,重來" << endl;
			break;
		case 3:
			cout << "電腦頭向左,沒輸沒贏,重來" << endl;
			break;
		case 4:
			cout << "電腦頭向右,沒輸沒贏,重來" << endl;
			break;
		}
	}
}

//黑白配函式之電腦回合
void achicomsturn(int n, Player p, Bot b) {
	int com3;
	com3 = 1 + rand() % 4;
	if (n == com3) {
		switch (com3) {
		case 1:
			cout << "電腦指上,電腦贏了,你輸了" << endl;
			b.scorePlus();
                      //電腦贏了,分數+1
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數  
			break;
		case 2:
			cout << "電腦指下,電腦贏了,你輸了" << endl;
			b.scorePlus();
                      //電腦贏了,分數+1
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數  
			break;
		case 3:
			cout << "電腦指左,電腦贏了,你輸了" << endl;
			b.scorePlus();
                      //電腦贏了,分數+1
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數  
			break;
		case 4:
			cout << "電腦指右,電腦贏了,你輸了" << endl;
			b.scorePlus();
                      //電腦贏了,分數+1
			cout << "目前比數: \n" << b.toString() << " : " << b.getScore() << " 分 | " << p.toString() << " : " << p.getScore() << " 分" << endl;
                      //顯示目前電腦以及玩家目前的比數  
			break;
		}
	}
	else {
		switch (com3) {
		case 1:
			cout << "電腦指上,沒輸沒贏,重來" << endl;
			break;
		case 2:
			cout << "電腦指下,沒輸沒贏,重來" << endl;
			break;
		case 3:
			cout << "電腦指左,沒輸沒贏,重來" << endl;
			break;
		case 4:
			cout << "電腦指右,沒輸沒贏,重來" << endl;
			break;
		}
	}
}

//防呆函式,防止玩家輸入規定以外的數字
void tenoyanncyann(int n, Player p, Bot b) {
	int hum2;
	cout << "手不要亂指!!\n";
	cout << "\n請重新輸入1(指上) 2(指下) 3(指左) 4(指右)：";
	cin >> hum2;
	if (hum2 == 1 || hum2 == 2 || hum2 == 3 || hum2 == 4) achi(hum2,p,b);
	else tenoyanncyann(hum2,p,b);
}

//防呆函式,防止玩家輸入規定以外的數字
void atamanoyanncyann(int n, Player p, Bot b) {
	int hum2;
	cout << "頭不要亂伸!!\n";
	cout << "\n請重新輸入1(頭往上) 2(頭往下) 3(頭往左) 4(頭往右)：";
	cin >> hum2;
	if (hum2 == 1 || hum2 == 2 || hum2 == 3 || hum2 == 4) achicomsturn(hum2,p,b);
	else atamanoyanncyann(hum2,p,b);
}

//main函式
int main() {

	int hum, com, hum2;
	bool isValidInput;
	string playersname;
	cout << "請輸入名字:" << endl;
	cin >> playersname;
	Player p(playersname);
            //輸入姓名並創造Player類別的物件
	Bot b;
            //創造Bot類別的電腦物件並與其進行遊戲
	
	srand(time(0));
  
	cout << "請輸入1(剪刀) 2(石頭) 3(布) 或 -1離開 ：";
	cin >> hum;
  
            //若輸入-1即結束遊戲,反之即進行遊戲
	while (hum != -1) {
            //輸入1個數字決定你所出的是什麼
		isValidInput = true;
		switch (hum) {
		case 1:
			cout << "你出的是剪刀" << endl;
			break;
		case 2:
			cout << "你出的是石頭" << endl;
			break;
		case 3:
			cout << "你出的是布" << endl;
			break;
		default:
			cout << "請不要亂出!!" << endl;
			isValidInput = false;
                      //防呆,若輸入了123以外的數字,則將isValidInput改為false
			break;
		}
    
                 //若isValidInput為false,下面的if函式將會被略過,直接跳到第298行
		if (isValidInput) {
			com = 1 + rand() % 3;
                      //亂數決定電腦出的是什麼
			switch (com) {
			case 1:
				cout << "電腦出的是剪刀" << endl;
				break;
			case 2:
				cout << "電腦出的是石頭" << endl;
				break;
			case 3:
				cout << "電腦出的是布" << endl;
				break;

			}
                      //下面決定猜拳是誰贏且決定黑白配是誰的回合
			switch ((hum - com + 3) % 3) {
			case 0:
				cout << "出一樣,重猜" << endl;
				break;
			case 1:
				cout << "你的回合" << endl;
				cout << "請輸入1(指上) 2(指下) 3(指左) 4(指右)：";
				cin >> hum2;
				if (hum2 == 1 || hum2 == 2 || hum2 == 3 || hum2 == 4)
                                  //若輸入的值為1,2,3,4,則進入黑白配函式之玩家的回合
					achi(hum2,p,b);
				else
                                  //若輸入的值為1,2,3,4以外的數字,則進入防呆函式
					tenoyanncyann(hum2,p,b);
				break;
			case 2:
				cout << "電腦的回合" << endl;
				cout << "請輸入1(頭往上) 2(頭往下) 3(頭往左) 4(頭往右)：";
				cin >> hum2;
				if (hum2 == 1 || hum2 == 2 || hum2 == 3 || hum2 == 4)
                                  //若輸入的值為1,2,3,4,則進入黑白配函式之電腦的回合
					achicomsturn(hum2,p,b);
				else
					atamanoyanncyann(hum2,p,b);
                                  //若輸入的值為1,2,3,4以外的數字,則進入防呆函式
				break;

			}
		}
		cout << "\n請輸入1(剪刀) 2(石頭) 3(布) 或 -1離開 ：";
		cin >> hum;
	}
        //若退出遊戲,則將玩家級電腦的分數歸零
	p.resetScore();
	b.resetScore();
}
```
