//#include <iostream>
#include<bits/stdc++.h>
#include<string>
using namespace std;

//struct Player {
//	int numPlayers ;
//	int  id;
//	string name  ;
//	string role  ;                But I just use only the class to handle this problem.
//	int	match_played ;
//	int	wikets ;
//	int	runs ;
//	int	play_innings ;
//};
static int inngs=0;
class Cricket {

		static const int NUM_FIELDS = 100;
		int  id[NUM_FIELDS];
		string name[NUM_FIELDS] ;
		string role[NUM_FIELDS] ;
		string team[NUM_FIELDS] ;
		int match_played[NUM_FIELDS];
		int runs[NUM_FIELDS];
		int Batsman_wickets[NUM_FIELDS];
		int wickets[NUM_FIELDS];
		int Bowler_runs[NUM_FIELDS];
		int mergeRuns[NUM_FIELDS];
		int numPlayers,highScore,highWkts;
		string  Batting="Batsman",Bowling="Bowler",Allrounder="BattingAllrounder";
		double Avg_runs,Bowl_Economy;
		string input13, yes="1",no="2";
		int min,max;


	public:

		void get_Player_data() {
			cout<<"Enter the Player you want to store in Data::";
			cin>>numPlayers;
			for (int i = 0; i < numPlayers; ++i) {
				cout<<"\n\t\t**********************  Player " <<"[ "<<i+1<<" ]"<< " Information **********************"<<endl;
				cout << "\nEnter the player's ID " << i + 1 << ": ";
				cin >> id[i];
				cout << "Enter the player's Name " << i + 1 << ": ";
				cin >> name[i];
				cout << "Enter the player's Role :"<< i + 1<<"  1)Batsman 2)Bowler 3)BattingAllrounder : ";
				cin >> role[i];
				cout << "Enter the player's Match Played " << i + 1 << ": ";
				cin >> match_played[i] ;

				int matchplayed=match_played[i];
				
				if(role[i]==Batting) 
				{
						cout<<"Enter the player's Runs "<<i+1<<":"<<endl;
					for(int i=0; i<matchplayed; i++) {

						do {
							cout <<"Match NO " << i + 1 << ": ";
							cin>>runs[i];
							inngs++;
							i++;
						} while(i!=matchplayed);



						cout<<"Player want to bowling in this match 1)Yes 2)No :"<<i+1<<":";
						cin>>input13;
						if(input13==yes) {
							int input1;
							cout<<" how much innges batsmen play :";
							cin>>input1;
							for(int i=0; i<input1; i++) {
								cout<<"Enter the wikets"<<i+1<<":";
								cin>>Batsman_wickets[i];
								inngs++;
							}
						}



					}

				}


				if(role[i]==Bowling) {

                    cout<<"Enter the player's Wickets "<<i+1<<":"<<endl;
					for(int i=0; i<matchplayed; i++) {

						do {
							cout<<"Enter the player's Wickets "<<i+1<<":"<<endl;
							cout <<"Match No Wickets" << i + 1 << ": ";
							cin>>wickets[i];
							inngs++;
							i++;
						} while(i!=matchplayed);

						cout<<"Player want to batting in this match 1)Yes 2)No :"<<i+1<<":";
						cin>>input13;
						if(input13==yes) {
							int input1;
							cout<<" how much innges bowler do batting play :";
							cin>>input1;
							for(int i=0; i<input1; i++) {
								cout<<"Enter the wikets"<<i+1<<":";
								cin>>Bowler_runs[i];
								inngs++;
							}
						}

					}
				}
				if(role[i]==Allrounder) {
					cout << "Enter the player's Runs " << i + 1 << ": ";
					for (int i = 0; i < matchplayed; ++i) {
						cout <<"Match NO " << i + 1 << ": ";
						cin>>runs[i];
					}

					cout << "Enter the player's Wickets " << i + 1 << ": ";
					for (int i = 0; i < matchplayed; ++i) {
						cout <<"Match No Wickets" << i + 1 << ": ";
					}



				}
				for(int i=0; i<matchplayed; i++) {
					mergeRuns[i]=runs[i];
				}
			//	min_max();


				cout<<"Which team does this player play for? 1)team Name 2)NA - "<<i+1<<":";
				cin >> team[i];

			}
				}


//		}
//		void min_max() {
//
//			max=mergeRuns[0];
//			min=mergeRuns[0];
//			for(int i=0; i<matchplayed; i++) {
//				if(max<mergeRuns[i])
//					max=mergeRuns[i];
//				else if(min>mergeRuns[i])
//					min=mergeRuns[i];
//
//			}
//
//			cout<<"\nMaximum Score :: "<<max;
//			cout<<"\nMinimum Score: "<<min;
//
//		}
		void  display_Data() 
		{
			for (int i = 0; i < numPlayers; ++i) {
				cout<<"\n\t\t**********************  Player " <<"[ "<<i+1<<" ]"<< " Information **********************"<<endl;
				cout << "\n Player's ID " << i + 1 << ": " <<id[i]<<endl;
				cout << " Player's Name " << i + 1 << ": "<<name[i]<<endl;
				cout << "Player Role" << i + 1 << ": "<< role[i]<<endl;
				cout << "Player's Match Played " << i + 1 << ": "<<match_played[i]<<endl;
				int m=match_played[i];
				 cout<<" Runs of the player :"<<endl;
				  	for(int i=0; i<m; i++) 
				  {
				      cout<<"Match No"<<i+1<<runs[i]<<endl;	
				  }
	
            }
		}

};



int main() {
	Cricket c1;
	c1.get_Player_data();
	c1.display_Data();



}


