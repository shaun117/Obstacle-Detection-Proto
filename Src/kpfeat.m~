function patches = kpfeat(img, feat)
% KPFEAT Extracts feature vectors from an image given the image and
% detected feature centers.
%
% patches = KPFEAT(img, feat) where img is a grayscale double image and
% feat is matrix where non-zero values correspond to detected features in
% img.
%
% Authors:
%   Kevin Lee (Box 4088)
%   Henry Nelson (Box 4214)
%
% Lab
%   Feature Descriptors
    [rows, cols] = find(feat);
    patches = zeros(length(rows), 9);
    gauss = gkern(5^2);
    blurred = conv2(gauss, gauss, img, 'same');
    downsize = blurred(1:5:end, 1:5:end);

    for k = 1:length(rows)
        r = round(rows(k)/5);% Downsized row of center
        c = round(cols(k)/5);% Downsized column of center
        if (((r-1) < 1)||((r+1) > size(downsize,1))||...
                ((c-1) < 1)||((c+1) > size(downsize,2)))
            
            patches(k,:) = NaN(1,9);
            continue;
        end
                
        patch = downsize(r-1:r+1,c-1:c+1);
    
        normalizedPatch = (patch - mean(patch(:)))/std(patch(:));
    
        patches(k,:) = normalizedPatch(:);
    end
    return
end

