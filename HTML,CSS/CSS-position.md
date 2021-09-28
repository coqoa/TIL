# CSS position
- position : static;  
top, bottom, left, right  
기본값  

- position : relative;
부모를 기준으로 top, bottom, left, right 값 만큼 이동  
부모가 이동하면 같이 움직인다  
값을 0 으로 하면 원위치  

- position : absolute;
부모로부터 자유로워진다 (공중부양)  
콘텐츠의 크기로 크기변경  
값을 0으로 하면 부모의 범위 내에서 이동 (* 부모가 static이 아닐때만)  
부모가 static이면 무시, 그 위의 부모기준 범위를 가진채로 이동한다  

- position : fixed;
absolute와 유사 (공주부양, 콘텐츠 크기로 크기변경)  
값을 주면 무조건 최상위 태그의 범위를 기준으로 이동한다  
스크롤을 무시한다  
