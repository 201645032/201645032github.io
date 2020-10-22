## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/201645032/201645032github.io/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown


package postTest;

import java.io.IOException;
import java.util.List;

public class postTest {

	/*
	 * 주요 로직: COMPLETEYN이 N이면 운송장 에러인지 확인하고, API 갱신하는 과정 거쳐서 출력해주고, Y면 출력화면으로 바로 뿌려준다.
	 * MVC모델의 특징을 이용해서 중복되는 기능없이 골고루 돌아가도록 작동시키는 것이 중요함.
	 */
	public static void main(String[] args) throws IOException {
		System.out.println("postTest: 작동시작 ");
		/* 서비스 호출 문제 없음 */
		postTrackingService trackingService = new postTrackingService();
		List<postTrackingVO> trackingList = trackingService.getPostInfo();
		postResponseInfo  responseInfo= new postResponseInfo();
		for (postTrackingVO postTracking : trackingList) {
			try {
				if (postTracking.getDLV_COMPLETEYN().equals("N")) {
				responseInfo.getResponse(postTracking.getDLV_CUST(), postTracking.getDLV_TRACKING_NO(),postTracking.getDLV_SEQ());
				}
				else {
					//시퀀스로 디테일에 해당되는 값 전부가져와서 뿌려주자...(HTML 동적 태그 이용..추후 예정)
					//조회화면으로 가죠..(서비스에)
				}
			} catch (Exception e) {
				System.out.println("postTest: 작동실패...");
			}
		}

	}

}

```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/201645032/201645032github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
