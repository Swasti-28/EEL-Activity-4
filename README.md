# EEL-Activity-4
#include <stdio.h>
struct Staff {
    int id;
    char name[30];
    int role; 
    float baseSalary;
    int experience;
    float totalSalary;
};
void main() {
    int n, i, j;
    struct Staff s[50], temp;
    printf("Enter number of staff members:\n ");
    scanf("%d", &n);
    printf("\nRole Codes:\n1=Surgeon\n2=Consultant\n3=Doctor\n4=Nurse");
    for(i=0; i<n; i++) {
        printf("\nEnter details for staff %d\n", i+1);
        printf("ID: ");
        scanf("%d", &s[i].id);
        printf("Name: ");
        scanf("%s", s[i].name);
        printf("Role Code: ");
        scanf("%d", &s[i].role);
        printf("Base Salary: ");
        scanf("%f", &s[i].baseSalary);
        printf("Experience (in years): ");
        scanf("%d", &s[i].experience);
        
        float bonus = 0;
        if(s[i].role == 1) {
            bonus = 15000;}
        else if(s[i].role == 2) {
            bonus = 12000;}
        else if(s[i].role == 3) {
            bonus = 10000;}
        else if(s[i].role == 4) {
            bonus = 7000;}
            s[i].totalSalary = s[i].baseSalary + bonus;
    }
    for(i=0; i<n-1; i++) {
        for(j=i+1; j<n; j++) {
            if(s[i].totalSalary < s[j].totalSalary ||
              (s[i].totalSalary == s[j].totalSalary && s[i].experience < s[j].experience)) {
                temp = s[i];
                s[i] = s[j];
                s[j] = temp;
            }
        }
    }
    printf("\n--- Hospital Staff Salary Details ---\n");
    for(i=0; i<n; i++) {
        printf("%d\t%s\t\t", s[i].id, s[i].name);
        if(s[i].role == 1) {
            printf("Surgeon\t\t");}
        else if(s[i].role == 2) {
            printf("Consultant\t\t"); }
        else if(s[i].role == 3) {
            printf("Doctor\t\t");}
        else if(s[i].role == 4) {
            printf("Nurse\t\t");}
            printf("%.2f\t\t%d\n", s[i].totalSalary, s[i].experience);
    } 
 }
