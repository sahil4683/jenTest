
https://chat.openai.com/share/fc8b6f56-ccb6-4954-b002-16e990ddabd3


https://chat.openai.com/share/c09c80b1-24fa-44be-8904-68ea1ff497d0

https://chat.openai.com/share/0a8ddd7f-5ee0-4a1d-bf77-4835408c25ad

// Component Code Teat
it(`should have a title 'I love pizza!'`, async(() => {
  fixture = TestBed.createComponent(PizzaComponent);
  component = fixture.debugElement.componentInstance;
  expect(component.title).toEqual('I love pizza!');
}));




// Api Call Test 
import { TestBed, async, inject } from '@angular/core/testing';
import { HttpClientTestingModule, HttpTestingController } from '@angular/common/http/testing';
import { PostService } from './post.service';
describe('PostService', () => {
  let postService: PostService;
  let httpMock: HttpTestingController;
  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        HttpClientTestingModule,
      ],
      providers: [
        PostService
      ],
    });
    postService = TestBed.get(PostService);
    httpMock = TestBed.get(HttpTestingController);
  });
  it(`should fetch posts as an Observable`, async(inject([HttpTestingController, PostService],
    (httpClient: HttpTestingController, postService: PostService) => {
      const postItem = [
        {
          "userId": 1,
          "id": 1,
          "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
          "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
        },
        {
          "userId": 1,
          "id": 2,
          "title": "qui est esse",
          "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
        },
        {
          "userId": 1,
          "id": 3,
          "title": "ea molestias quasi exercitationem repellat qui ipsa sit aut",
          "body": "et iusto sed quo iure\nvoluptatem occaecati omnis eligendi aut ad\nvoluptatem doloribus vel accusantium quis pariatur\nmolestiae porro eius odio et labore et velit aut"
        }
      ];

      postService.getPosts()
        .subscribe((posts: any) => {
          expect(posts.length).toBe(3);
        });
      let req = httpMock.expectOne('https://jsonplaceholder.typicode.com/posts');
      expect(req.request.method).toBe("GET");
      req.flush(postItem);
      httpMock.verify();
    })));
});




