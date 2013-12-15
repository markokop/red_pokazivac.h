red_pokazivac.h
===============

struct tpacijent{
       char ime[15], prezime[20];
       int dan, mjesec, godina;
       char spol;
       int dolazak, u_ordinaciji;
       int prioritet;
       int usluga;
       int ordinacija;
       };
       
struct qu{
       tpacijent pacijent;
       qu *sljedeci;
       };
       
struct que{
       qu *front, *rear;
       };
       
typedef que tqueue;
typedef qu *element;

bool IsEmptyQ(tqueue *queue){
     if (queue->rear==queue->front) return 1;
        else return 0;
     }
     
tpacijent FrontQ(tqueue *queue){
     if (!IsEmptyQ(queue)) return queue->front->sljedeci->pacijent;
     }
          
void InitQ(tqueue *queue){
     queue=new tqueue;
     qu *stari=new qu;
     queue->front=stari;
     queue->rear=stari;
     stari->sljedeci=NULL;
     }
     
void DeQueueQ(tqueue *queue){
     if (!IsEmptyQ(queue)){
        qu *stari;
        stari=queue->front;
        queue->front=stari->sljedeci;
        delete stari;
        }
     }
     
void EnQueueQ(tpacijent x, tqueue *queue){
     qu *novi = new qu;
     novi->sljedeci=NULL;
     queue->rear->sljedeci=novi;
     queue->rear=novi;
     novi->pacijent=x;
     }
